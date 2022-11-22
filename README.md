# Introduction to Tornado Cash

![](.gitbook/assets/image.png)

Tornado Cashは暗号空間でプライベートトランザクションを可能にする**完全に分散化されたノンカストディアルのプロトコル**です。

分散型プロトコルであるTornado Cashのスマートコントラクトは、Ethereumブロックチェーンに実装されているためイミュータブルなものとなっています。それらは変更も改竄もできません。したがって、オリジナルの開発者を含め誰もそれを変更したり停止したりすることはできません。すべてのガバナンスとマイニングのスマートコントラクトはコミュニティによって非中央集権的にデプロイされています。

ノンカストディアルのプロトコルとして、ユーザーはTornado Cashを操作している間、自分の暗号通貨のカストディを維持します。これは、各デポジットにおいてデポジットされた資金へのアクセスを可能にする秘密鍵が提供されることを意味し、これによりユーザーは自分の資産を完全に管理することができます。

## プライバシーはどのように実現されるのか？

Tornado Cashは、送信元アドレスと送信先アドレスの間のオンチェーンリンクを解除することでトランザクションのプライバシーを向上させます。これには、あるアドレスからETHと他のトークンのデポジットを受け入れ、別のアドレスからそのデポジットを引き出すことを可能にするスマートコントラクトを使用しています。

プライバシーを最大限に守るため、あらかじめ残高のないアドレスから資金を引き出せるようにガス料金の支払いにはリレイヤーを使用するなど、いくつかのステップを踏むことが推奨されます。

詳細は[*How does Tornado Cash work?*](general/how-does-tornado.cash-work.md)と[Tips to remain anonymous](general/tips-to-remain-anonymous.md)に掲載されています。

## Tornado Cashはどこで稼働しているのか？

2019年の誕生以来、Tornado Cashは**Ethereumブロックチェーンで**運用されています。このプロトコルはEthereumのブロックチェーンで扱われる6つのトークン（ETH、DAI、cDAI、USDC、USDT、WBTC）に対して多様な定額プールを提供してきました。

2021年6月以降、Tornado CashのスマートコントラクトはEthereumブロックチェーンに加え**他のサイドチェーン＆ブロックチェーンにもデプロイされています**。これらのデプロイにより、新しいトークンのサポート、また、より高速で安価な取引といったレイヤー2の利点を享受することができるようになりました。

現在、Tornado Cashは以下で運用されています。

* **Ethereum Blockchain** : **ETH** (Ethereum)、**DAI** (Dai)、**cDAI** (Compound Dai)、**USDC** (USD Coin)、**USDT** (Tether) **WBTC** (Wrapped Bitcoin)
* **Binance Smart Chain**：**BNB** (Binance Coin)
* **Polygon Network**：**MATIC** (Polygon)

* **Gnosis Chain (former xDAI Chain)**：**xDAI** (xDai)
* **Avalanche Mainnet**：**AVAX** (Avalanche)
* **ETH** (Ethereum) のLayer-2として、**Optimism**
* **ETH** (Ethereum) のLayer-2として、**Arbitrum One**

![](.gitbook/assets/logos.png)

2021年12月まで、このプロトコルにはこれらのトークンの一部に対する匿名マイニングシステムが含まれており、そのユーザーはガバナンストークン（**TORN**）を獲得することができました。ユーザーは最終的にETH、DAI、cDAI、WBTCのプールにデポジットすることで、ブロックチェーンネットワーク上でTORNを獲得することができたのです。

*詳しくは*[*Anonymity mining*](tornado-cash-classic/anonymity-mining.md)*と*[*Tornado Cash token*](general/torn.md)を参照してください。

**TORNトークンのおかげで、Tornado Cashユーザーはプロトコルの形成に積極的に参加することができます。** コミュニティはTornado Cashの進化とその機能の改善に関して強いウェイトを占めています。実際、プロトコルのパラメータとトークンの配布はこのガバナンスを通じて完全にコミュニティの管理下にあります。

上記のすべてのプールは、[tornadocash.eth.link](https://tornadocash.eth.link)でアクセスできます。それらは**定額デポジット・定額引き出しの原則で**を運用されています。これは、各トークンが2～4種類のプールを持ち、2～4種類の固定金額のみのトランザクションを可能にするということです *（例えば、ETHには0.1、1、10、100 ETHの4種類のプールがあります）* 。

### Tornado Cash Nova

[2021年12月の**Tornado Cash Nova**（ベータ版）のリリース](https://tornado-cash.medium.com/tornado-cash-introduces-arbitrary-amounts-shielded-transfers-8df92d93c37c)に伴い、**ユニークな新機能を備えたグレードアップしたプール**がプロトコルに追加されました。ユーザーはもはや固定額取引に縛られることはありません。Tornado Cash Novaの登場により、**任意の金額のプールとシールドされた送金**による恩恵を受けることができます。

Tornado Cash Novaは、Gnosis Chain（旧xDai Chain）上でLayer2として動作し、スピードとコストを最適化します。これにより、**完全にカスタマイズされた金額のETHを入出金**ができます。また、このプールでは、ユーザーが**transfer the custody of their token while remaining in the pool**できるシールドされたトランザクションが可能です。

Tornado Cash Nova（ベータ版）は、[nova.tornadocash.eth.link](https://nova.tornadocash.eth.link)でアクセスできます。Tornado Cash Novaの機能に関する詳しい情報は、私たちのドキュメントの専用セクションを参照してください。

## Tornado Cashはどのように動作するのか？

[Tornado Cashの機能を実現するためのコード](https://github.com/tornadocash)（スマートコンタクト、回路＆ツールチェーンなど）は完全に**オープンソース**です。DAO (Decentralized Autonomous Organization)によって、Tornado Cashガバナンスとマイニングスマートコントラクトは、そのコミュニティによってデプロイされています。

また、zk-SNARKを用いることで、情報を明らかにすることなく、その情報を所有していることを証明することができます。この技術の使用は**ZcashチームがEthereumコミュニティの協力を得て行ったオープンソースの研究**をベースにしています。zk-SNARKの初期鍵を設定するために、2020年5月にTornado Cash [ Trusted Setup Community](https://tornado-cash.medium.com/tornado-cash-trusted-setup-ceremony-b846e1e00be1)が誕生し、これには[1114人のコントリビューター](https://tornado-cash.medium.com/the-biggest-trusted-setup-ceremony-in-the-world-3c6ab9c8fffa)のアカウントが含まれています。このようにたくさんのコントリビューターがいるため、ゼロ知識証明を偽造してプロトコルを危険にさらすことは不可能です。

ユーザーインターフェースは、コミュニティによって**IPFS** (InterPlanetary File System)上でホストされており、データ削除のリスクを最小限に抑えています。実際、少なくとも一人のユーザーがホスティングしている限り、インターフェースは動作します。

*Written & updated by* [*@ayefda*](https://torn.community/u/ayefda)

