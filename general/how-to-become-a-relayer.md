# How to become a relayer?
[Tornado Cash 10th governance proposal](https://tornadocash.eth.link/governance/10)の実行により、誰でもトルネードキャッシュのユーザーの中継者となることができる。

{% hint style="success" %}
トルネードキャッシュのUIに掲載されるための唯一の条件は、最低`300 TORN`件*のトルネードをロックすることです。上場維持のためには、ステーク契約に対して取引手数料を返済できるだけのTORNをロック（2022年4月現在、 \~`40 TORN` ）しておく必要がある。
{endhint %}。

\**This minimum stake can be changed by a governance vote at any time.*

中継器は、Tornado Cashのエコシステムにおいて必要不可欠なものです。リレーヤーは、悪名高い「手数料支払いのジレンマ」を解決し、匿名性を維持しながらプールからのトークン引き出しのための手数料を支払う方法として、プライバシーを保証するものです。

そのため、中継者は第三者として、出金全体を管理する。取引手数料は、送金額から直接差し引かれる。また、そのサービスには別途手数料がかかる。

[Relayer Registry proposal](https://tornadocash.eth.link/governance/10)の実装以来、プロトコルは引き出しごとに`StakingReward`契約を通じて中継者のステークドバランスから直接手数料を徴収しています。この手数料の割合はプールごとに異なる場合があり、また、オンチェーンガバナンスによって変更される場合があります。

現在、それは`0.3%`に固定されています。いくつかのプールは、手数料を割り当てるにはインスタンスが小さすぎるため（0.1ETH、100DAI/USDT、1000DAI/USDT）、またはUni v3（すべてのcDAIインスタンス）に十分な流動性がないため、手数料なしで残っています。

## How to Become a Relayer?
誰でも[Relayer Registry User Interface (UI)](https://relayers-network.tornadocash.eth.limo)を介して**6 simple steps**のプロトコルの中継者になることができる。

以下に、私たちの中継者クラブに参加し、Tornado Cashの分散型中継者レジストリに登録するために必要なものがすべて揃っています。

### 1. Warning: Understand & Accept Potential Risks
中継者としてトルネードキャッシュのユーザーと旅の一部を共有することを約束する前に、プロトコルの中継者になることの潜在的なリスクをすべて理解し、受け入れる必要があります。

#### How a Relayer is chosen by user interface
中継器の指定式は以下の通りです。

* 登録された全中継者のリストは、Relayer Registryスマートコントラクトから取得される。

* 各リレーヤーについて、賭け金であるTORNと手数料を基にスコアを計算する。ステークが高いほどスコアは高くなり、手数料が高いほどスコアは低くなる。Ethereumメインネットの場合、スコアの計算式は`stake * [1 - 25*(fee-0.33)^2]`、サイドチェーンの場合、計算式は`stake * [1 - 11.89*(fee-0.01)^2]`である。

* 次に、計算されたスコアで重み付けされたリレーヤをランダムに選ぶ。

### 2. Set up Relayer
具体的な最初のステップは、Ethereum Mainnet 用の Tornado Cash Relayer ソフトウェアをコンピュータで実行することです。すべての手順は、プロトコルの github にまとめられています。この作業を成功させるためには、[these instructions](https://github.com/tornadocash/tornado-relayer#deploy-with-docker-compose)に注意深く従う必要があります。

{% embed url="https://github.com/tornadocash/tornado-relayer#deploy-with-docker-compose" %}.

入力が完了したら、入力ボックスにurlを挿入してください。

![](<../.gitbook/assets/2 (1).png>)

{ヒント スタイル="警告" %}。
独自の RPC ノードを使用することを強くお勧めします。フルノードの実行方法については、[here](https://github.com/feshchenkod/rpc-nodes)を参照してください。
{endhint %} を参照してください。

### 3. Set Up ENS Subdomain
次のステップは、次のようなものです。

* リレイヤーのENSドメインを作成する。

* そのメインネットのサブドメインを設定する。

* この特定の形式に従って、RelayerのURLを含むTXTレコードをメインネットサブドメインに追加すること。

#### **Ethereum Relayers (Mandatory)**
|TXT record|
|-|
|mainnet-tornado.xxx.eth|
|goerli-tornado.xxx.eth|

#### **Sidechains Relayers (Optional)**
また、Ethereum以外のチェーンをサポートするために、対応するTXTレコードを持つサブドメインを追加するオプションもあります。サイドチェーンリレーヤーは、リレーヤーソフトウェアの異なるバージョンを使用します。インストラクションを含む完全な要件は、[here](https://github.com/tornadocash/tornado-relayer/blob/light/README.md)を参照してください。

|TXT record|
|-|
|bsc-tornado.xxx.eth|
|gnosis-tornado.xxx.eth|
|polygon-tornado.xxx.eth|
|optimism-tornado.xxx.eth|
|arbitrum-tornado.xxx.eth|
|avalanche-tornado.xxx.eth|

#### **Nova Relayer (Optional)**
トルネード・キャッシュ・ノヴァは独自のバージョンを使用しています。もし、トルネードキャッシュ・ノヴァの中継者になりたい場合は、[here](https://github.com/tornadocash/tornado-pool-relayer#deploy-with-docker-compose)に従うように指示があります。

|TXT record|
|-|
|gnosis-nova.xxx.eth|

![](../.gitbook/assets/3.png)

### **4. Set Up Workers**
ワーカーは、リレイヤーがユーザーにZKプルーフを送信するためのアドレスです。デフォルトでは、最初のワーカーはENSドメイン所有者のアドレスになります。

より高いセキュリティを確保するために、ワーカーを複数設定することをお勧めします。

メインネットのみワーカーを登録する必要があります。その他のネットワークでは、登録されたワーカーの使用は必要ありません。

![](../.gitbook/assets/4.png)

### 5. Stake
分散型中継者レジストリの実装に伴い、Tornado Cash UIに上場するための条件としてステーキング条件が導入されました。**staking TORN is now necessary to be added to the recommended list of relayers.**に留意してください。

最低賭け金額は、現在Tornado Cashのガバナンスによって**`300 TORN`**に設定されています。この閾値はTornado Cashガバナンスによっていつでも変更することができる。

中継者が Tornado Cash プールで使用されると、`StakingReward` 契約によってこのステーク残高から少量の TORN が自動的に徴収される。この要素は、中継者がステーキングコントラクトに取引手数料を返済できるだけのTORN（2022年4月時点では" \~`40 TORN`" ）をロックしておく必要があるため、覚えておくことが重要である。

集められた手数料は、その後、ロックされたTORNトークンでDAOメンバーに分配されます。TORNは通常、オンチェーンガバナンス（提案の提出と投票）に参加するためにロックされています。この[forum post](https://torn.community/t/proposal-relayer-registry-setting-parameters-after-audit/2134)と[Staking TORN documentation page](staking/)の両方でより多くの情報を見つけることができます。

{ヒント スタイル="警告" %}。
賭けられたTORNの金額は請求できませんし、払い戻しもできません。
{% endhint %}

![](../.gitbook/assets/5.png)

### 6. Summary: Final Verification & Registration
最後になりますが、登録する前に「概要」に表示されている**double-check all information**を確認することをお勧めします。

![](../.gitbook/assets/6.png)

*Welcome to the relayer team! Thanks to you, privacy can be better respected* 💚

x00 x03 x04 x07

