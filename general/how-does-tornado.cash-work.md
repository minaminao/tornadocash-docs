# How Does Tornado Cash Work?
Tornado.Cashの使い方を説明するチュートリアルに入る前に、プロトコルのグローバルな機能についての全体的な概要を説明します。

### Global overview of Tornado.Cash functioning
プライバシーを実現するために、Tornado.Cash **uses smart contracts that accept token deposits from one address and enable their withdrawal from a different address**.それらのスマートコントラクトは、預けたすべての資産を混合するプールとして機能する。

これらのプールから完全に新しいアドレスによって資金が引き出されると、ソースと宛先の間のオンチェーンリンクが切断されます。そのため、引き出された暗号資産は匿名化されます。

トークンがTornado Cashプールにある間、親権はユーザーの手元に残ります。したがって、ユーザーは自分のトークンを完全にコントロールすることができます。

**For traditional Tornado Cash fixed-amount pools**:

* ユーザーが資金をプールに入れる（預ける）と、プライベートノートが生成されます。このプライベートノートは、そのユーザーが後で資金にアクセスするための秘密鍵として機能します。資金を引き出すには、同じユーザーが別のアドレス（古いアドレスでも新しいアドレスでも）を使用し、この秘密鍵のおかげで資金を回収することができます。

**For Tornado Cash Nova, the new ETH pool with arbitrary amounts & shielded transfers**:

* 資金は、指定されたウォレットアドレスに直接リンクされています。プライベートノートやキーは存在しません。ユーザーは、適切なアドレスでプールに接続することで、資金にアクセスすることができます。

* カストディは、トークンをプールに預ける行為、またはプールに登録し、他のアドレスから遮蔽された転送を受け取ることによって取得されます。

このようなプロトコルの強さは、ユーザー数とそのプールのサイズに直接リンクしています。より多くのユーザーがプールに入金すればするほど、その効果は大きくなります。しかし、プライバシーと匿名性を維持するために、ユーザーは以下のような基本的なルールを心に留めておく必要があります。

* 出金時のガス代支払いに中継器を使用。

* 入金＆出金操作の間に時間が経過することを許容する。

* 資産を回収するまでに何度か取引を行い、資金を群衆と混合させること。

*More recommendations are provided in:* [*Tips to remain anonymous*](tips-to-remain-anonymous.md)*.*

### Contribution of zk-SNARK & hashing process
Tornado.Cashは、ゼロ知識簡潔非対話的知識論証（zk-SNARKとも呼ばれる）を使用して、取引を検証し許可しています。

入金を処理するために、Tornado.Cashはバイトのランダムな領域を生成し、[Pedersen Hash](https://iden3-docs.readthedocs.io/en/latest/iden3_repos/research/publications/zkproof-standards-workshop-2/pedersen-hash/pedersen.html)（zk-SNARKsと友好的であるため）を介してそれを計算し、次にトークンと20 MiMCハッシュをスマートコントラクトに送ります。その後、コントラクトはそれをメルクルツリーに挿入する。

引き出し処理を行うために、同じ領域のバイトを、片方の**secret**ともう片方の**nullifier**に分割する。ヌリファイはハッシュ化される。このヌリファイは、スマートコントラクト＆メルクルツリーデータと照合するために、オンチェーンに送信されるパブリックインプットである。例えば二重消費を回避することができる。

zk-SNARKにより、初期コミットメントとヌリファイアの20MiMCハッシュを、情報を一切開示することなく証明することが可能です。ヌリファイヤーが公開されていても、ハッシュ化されたヌリファイヤーとイニシャルコミットメントを結びつける方法がないため、プライバシーが維持されます。さらに、取引に関する情報がMerkleルートに存在する場合でも、正確なMerkleパスに関する情報、ひいては取引の場所は非公開に保たれる。

入金は技術的には簡単ですが、20MiMCハッシュの計算とMerkle木の更新が必要なため、ガス代は高くなります。一方、出金処理は複雑ですが、ガスはヌリファイヤーハッシュとゼロ知識証明にのみ必要なため、安価に済みます。

*Written & updated by* [*@ayefda*](https://torn.community/u/ayefda)

