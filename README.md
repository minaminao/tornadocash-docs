# Introduction to Tornado Cash
![](.gitbook/assets/image.png)

Tornado Cash は、暗号空間での私的な取引を可能にする **fully decentralized** **non-custodial** **protocol** です。

分散型プロトコルであるTornado.Cashのスマートコントラクトは、Ethereumブロックチェーン内に実装されているため、不変のものとなっています。それらは変更も改ざんもできない。したがって、オリジナルの開発者を含め、誰もそれを変更したり停止したりすることはできません。すべてのガバナンスとマイニングのスマートコントラクトは、コミュニティによって分散的に展開されます。

非保護プロトコルとして、ユーザーはTornado.Cashを操作している間、彼らの暗号通貨の保管を維持します。これは、各預金において、入金された資金へのアクセスを可能にする秘密鍵が提供されることを意味し、これによりユーザーは自分の資産を完全に管理することができます。

## How is privacy achieved?
Tornado Cashは、送信元アドレスと送信先アドレスの間のオンチェーンリンクを解除することで、取引のプライバシーを向上させます。これは、あるアドレスからETHと他のトークンの預金を受け入れ、別のアドレスからその預金を引き出すことを可能にするスマートコントラクトを使用しています。

プライバシーを最大限に守るため、ガス料金の支払いには、あらかじめ残高のないアドレスから資金を引き出すための中継器を使用するなど、いくつかのステップを踏むことが推奨されます。

詳細は*Behind the scenes:* [*How does Tornado.Cash work?*](general/how-does-tornado.cash-work.md) & [Tips to remain anonymous](general/tips-to-remain-anonymous.md)に掲載されています。

## Where does Tornado.cash operate?
2019年の創業以来、トルネードキャッシュは**on the Ethereum blockchain**を運用してきました。このプロトコルは、イーサリアムのブロックチェーンで扱われる6つのトークン（ETH、DAI、cDAI、USDC、USDT＆WBTC）に対して、多様な定額プールを提供してきました。

2021年6月以降、イーサリアムブロックチェーンに加え、トルネードキャッシュのスマートコントラクト**have also been deployed on other side-chains & blockchains**.これらの展開により、このツールは新しいトークンをサポートするか、より高速で安価な取引といったレイヤー2の利点を享受することができるようになりました。

今日現在、トルネード・キャッシュは、次のように運用されています。

* **Ethereum Blockchain** : **ETH**（イーサリアム）、**DAI**（ダイ）、**cDAI**（コンパウンドダイ）、**USDC**（米ドルコイン）、**USDT**（テザー）＆**WBTC**（ラップドビットコイン）です。

* **Binance Smart Chain**：**BNB**（バイナンスコイン）。

* **Polygon Network**：**MATIC**（ポリゴン）。

* **Gnosis Chain (former xDAI Chain)**：**xDAI**（xDai）．

* **Avalanche Mainnet**：**AVAX**（アバランチ）。

* **ETH**（Ethereum）のLayer-2として、**Optimism**。

* **Arbitrum One**、Layer-2の**ETH**（Ethereum）として。

![](.gitbook/assets/logos.png)

2021年12月まで、このプロトコルには、これらのトークンの一部に対する匿名マイニングシステムが含まれており、そのユーザーはガバナンストークン（**TORN**）を獲得することができました。ユーザーは最終的にETH、DAI、cDAI＆WBTCのプールに入金することで、ブロックチェーンネットワーク上でTORNを獲得することができたのです。

*More information on* [*Anonymity mining*](tornado-cash-classic/anonymity-mining.md) *&* [*Tornado.Cash token*](general/torn.md)は*available.*です。

**Thanks to the TORN token, Tornado Cash users can actively participate in shaping the protocol**.コミュニティは、Tornado Cashの進化とその機能の改善に関して強いウェイトを占めています。実際、プロトコルのパラメータとトークンの配布は、このガバナンスを通じて完全にコミュニティの管理下にあります。

上記のすべてのプールは、[tornadocash.eth.link](https://tornadocash.eth.link)でアクセスできます。それらは**under the principle of fixed-amount deposits & withdrawals**を操作する。各トークンが2～4種類のプールを持ち、2～4種類の固定金額*(e.g. ETH has four different pools, one for each of these amounts: 0.1, 1, 10 & 100 ETH)*のみの取引を可能にするということです。

### Tornado Cash Nova
[**release of Tornado Cash Nova** (beta version) on December 2021](https://tornado-cash.medium.com/tornado-cash-introduces-arbitrary-amounts-shielded-transfers-8df92d93c37c)に伴い、**upgraded pool with unique new features**がプロトコルに追加されました。ユーザーは、もはや固定額取引に縛られることはありません。トルネード・キャッシュ・ノヴァの追加により、**an arbitrary amount pool & shielded transfers**の使用による恩恵を受けることができる。

Tornado Cash Novaは、Gnosis Chain（旧xDai Chain）上でLayer2として動作し、スピードとコストを最適化します。これにより、**deposits and withdrawals of completely customized amounts in ETH**.また、このプールでは、ユーザーが**transfer the custody of their token while remaining in the pool**できる遮蔽された取引が可能である。

トルネードキャッシュ・ノヴァ（ベータ版）は、[nova.tornadocash.eth.link](https://nova.tornadocash.eth.link)でアクセスできます。トルネードキャッシュ・ノヴァの機能に関する詳しい情報は、私たちのドキュメントの専用セクションを参照してください。

## How does Tornado.Cash run?
[Codes behind Tornado.Cash functioning](https://github.com/tornadocash) - スマートコンタクト、サーキット＆ツールチェーン - は完全に**open-sourced.** DAO（分散型自律組織）として動作し、Tornado.Cashガバナンスと採掘スマートコントラクトは、そのコミュニティによって展開されます。

また、zk-SNARKを用いることで、情報を明らかにすることなく、その情報を所有していることを証明することができる。この技術の使用は**on open-source research made by Zcash team with the help of the Ethereum community**をベースにしています。zk-SNARKの初期鍵を設定するために、2020年5月にTornado.Cash[ Trusted Setup Community](https://tornado-cash.medium.com/tornado-cash-trusted-setup-ceremony-b846e1e00be1)を立ち上げ＆アカウント[for 1114 contributions](https://tornado-cash.medium.com/the-biggest-trusted-setup-ceremony-in-the-world-3c6ab9c8fffa)。このように相当数の貢献者がいるため、ゼロ知識証明を偽造してプロトコルを危険にさらすことは不可能である。

ユーザーインターフェースは、コミュニティによって**IPFS** (InterPlanetary File System)上でホストされており、データ削除のリスクを最小限に抑えています。実際、少なくとも一人のユーザーがホスティングしている限り、インターフェースは動作します。

*Written & updated by* [*@ayefda*](https://torn.community/u/ayefda)

