# 回路

Tornado Cashのフロントエンドの背後には、Tornado Cashユーザーが得られるプライバシー保証を可能にする[Circom](https://docs.circom.io)回路がいくつも存在します。これらの回路は、ユーザーのデポジットに関するクレーム（有効であること、すでに引き出されていないこと、匿名マイニングの文脈でノートのデポジットトランザクションとその引き出しとの間に存在するブロック数など）を証明するためのインターフェイスとなる[ゼロ知識プロトコル](https://en.wikipedia.org/wiki/Zero-knowledge_proof)を実装しています。

### ZK回路の仕組み

#### SNARKsとGROTH16

Tornado Cashの仕組みを理解する前に、まずゼロ知識回路とその構築方法、クライアントサイドでの証明の生成方法、そしてオンチェーンでの検証方法を理解する必要があります。ZKシステムには[いくつかの異なるタイプ](https://en.wikipedia.org/wiki/Zero-knowledge_proof#Zero_knowledge_types)がありますが、Tornado Cashは「Succinct Non-interactive ARguments of Knowledge」（SNARK）と呼ばれるもの、特にGROTH16と呼ばれるものに依存しています。

#### Circomとsnarkjs

私たちは皆Vitalikではないので、このような複雑な多項式コミットメントの生成と実行を抽象化するような簡単なツールがあればベストでしょう。そこで、[Circom](https://docs.circom.io)と[snarkjs](https://github.com/iden3/snarkjs)の出番です。

Circomは回路言語のコンパイラと考えるのが最も簡単で、電気技師が電気回路を記述するのに使う[ハードウェア記述言語](https://en.wikipedia.org/wiki/Hardware_description_language)のような働きをします。ただし、電気回路の代わりに、コンポーネントとその接続方法を含む**算術回路**を記述しています。

Circomの回路をコンパイルすると、結果として[R1CS](https://docs.circom.io/1.-an-introduction/background#rank-1-constraint-system)と[Wasm](https://en.wikipedia.org/wiki/WebAssembly)の実行ファイルが出力され、それを使って[witness](https://docs.circom.io/1.-an-introduction/background#witness)が生成されます。

**R1CS**

R1CS（Rank-1 Constraint System）を理解するためには、もちろんもっと多くの数学が必要です。そして、重要な暗号システムの数学があるところには、[Vitalikの記事](https://medium.com/@VitalikButerin/quadratic-arithmetic-programs-from-zero-to-hero-f6d558cea649#5539)があるのです。

> R1CSは3つのベクトルの列 $(a, b, c)$ であり、R1CSの解はベクトル $s$ で、 $s$ は方程式 $s . a * s . b - s . c = 0$ を満たす必要があります。ここで $.$ は内積を表し、簡単に言えば、$a$と$s$を「同じ位置」で掛け合わせその和をとります。$b$と$s$、$c$と$s$を同様にすると、3番目の結果は最初の2つの結果の積に等しくなります。
>
> 次のステップでは、このR1CSをQAP形式に変換します。これは、ドット積の代わりに多項式を使う以外は、まったく同じロジックを実装しています...R1CSの制約を個別にチェックする代わりに、多項式でドット積チェックを行うことにより、すべての制約を同時にチェックできるようになりました。
>
> このQAP解の元になっているR1CS解の変数を、例えば最後の変数を30ではなく31にするなどして改竄しようとすると、$t$多項式のチェックに失敗することになります。

つまり、R1CSは回路が生成する証明が満たさなければならない多項式制約の集合です。これらの制約は回路設計における様々な「信号」と「演算」の関係に基づいて[Circomによって生成](https://docs.circom.io/2.-circom-fundamentals/constraints-generation)されています。

**Witnesses**

さて、Tornado Cashの使用目的によっては、witnessを必要としないかもしれません。しかし、心配しないでください。すべてが正しく機能していれば、Tornado Cashとのやり取りのwitnessはすべて、積極的に圧縮されその体はあなたの好きなように処分されます。

SNARK回路の文脈では、ウィットネスとは、回路が課すすべての制約を満たすために、回路設計に基づいて回路への入力から生成する必要のある値の集合です。Circomが生成するウィットネスジェネレータは、入力を回路に通して実行し、その過程で生成されるさまざまな中間値をすべてスナップショットする回路固有の解凍関数であると考えることができます。

このように入力から生成された展開図があれば、R1CSで指定された制約にどの値を代入すれば有効な証明となるかがわかります。

**Proof**

「証明」というと、「何かが真実であることを疑う余地のない形で保証すること」を想像するのではないでしょうか。しかしSNARKの文脈では、「証明」は実際には「*ほぼ間違いなく*真である」という*argument*を表しています。回路が課す多項式制約の解をいちいち伝えようとすると、回路内の中間状態の値の間にある種の関係が成立することを示すだけで、桁違いに大きな証明になってしまうのです。

任意の回路に対して、十分な計算能力を持つ人が回路の制約を満たす証明を不正な方法で生成することは可能ですが、それは[大きな素数の因数分解](https://en.wikipedia.org/wiki/RSA_Factoring_Challenge)とほぼ同等の難しさです。

つまり、SNARK回路の証明を生成する場合、与えられた入力に対する回路の中間状態を計算し（witness生成）、入力と中間状態、そして回路の出力の関係を計算することになります。

必要な制約条件を満たしたという証明ができたら、その証明と入出力の一部（公開信号）を公開することができます。R1CS、公開信号、証明、回路の証明鍵がわかれば、誰でも証明がR1CSを満たしていること、そして公開信号が証明に対応すると予想されるものであることを検証することができます。

### 回路

そのZK証明回路をよく理解した上で、Tornado Cashが比較的簡単な回路を使って、パブリックブロックチェーンネットワーク上で自分の入出金取引の関係を非公開かつパーミッションレスで曖昧にし、その後で入出金の関係（例えば、出金前にどれだけ待ったか）を証明することを方法を掘り下げましょう。

Tornado Cashは、2つの独立した主要な構成要素を持っていると理解するのがベストです。

#### コアデポジットコントラクト

コアとなるデポジット回路は、多くのユーザーが利用するもので、ユーザーがある資産額の預金を表すコミットメントを作成したこと、その資産をまだ引き出していないこと、最初のコミットメントを作成したときに提供した秘密を知っていることを証明するものである。

{% content-ref url="core-deposit-circuit.md" %}
[core-deposit-circuit.md](core-deposit-circuit.md)
{% endcontent-ref %}

#### 匿名マイニング

匿名マイニング回路は、匿名マイニングプログラムの基礎を形成し、Tornado Cashのデポジットプールが多数のアクティブなデポジットを維持する（したがって、他のユーザーの[k-anonymity](https://en.wikipedia.org/wiki/K-anonymity)を増やす）ように、ユーザーがコントラクト内でより長い期間デポジットを残すインセンティブを与えています。

{% content-ref url="anonymity-mining/" %}
[anonymity-mining](anonymity-mining/)
{% endcontent-ref %}

