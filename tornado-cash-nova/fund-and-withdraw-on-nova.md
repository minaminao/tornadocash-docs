# Fund & Withdraw on Nova
Tornado Cashは、送金元と送金先のアドレス間のオンチェーンリンクを破壊することで機能します。そのため、このプロトコルでは、あるアドレスからトークンをプールに預け入れ、別のアドレスから引き出す必要があります。

この原則は、トルネード・キャッシュ・ノヴァでも変わりません。従来の定額制プールと同様に、この2つの動作はツールの効率性の核となるものである。

* 資金調達」のプロセス。

* 撤退」すること。

## Funding Process <a href="#funding-process" id="funding-process"></a>
従来のTornadoキャッシュプールと比べ、**deposited amounts are no longer predefined.**ユーザーはウォレット残高の範囲内でカスタマイズされた金額を選択することができるのが大きな特徴です。

したがって、0.4ETHをプールに入れたい場合、従来の0.1ETHプールで4回に分けて取引するのではなく、一度にまとめて取引することができます。

![](https://i.imgur.com/rqmzdgG.gif)

### How Does It Work? <a href="#how-does-it-work" id="how-does-it-work"></a>
#### **The First Deposit 💰**
* まず、メタマスクアカウントからトルネードキャッシュノヴァにログインします。

* あなたのアカウントはまだ設定されていません（右上のボタン`Set up account`が利用可能です）。アカウントを設定するには、次のいずれかの方法があります。

  * **Click on `Set up account`**：ログインしたアドレスは、トークンを預けることなく、ノヴァに登録されます。このアクションにより、他のアドレスからプール内の送金や預金を受け取ることができるようになります。

  * **Choose your logged-in address as a recepient address**: トークンをプールに預けることで、あなたのアカウント（シールドされたアドレスとシールドされたキー）が自動的に作成されます。入金された資金は、あなたのシールドされた残高に補充されます。

  * **Choose another registered address:**トークンは、選択された受信者アドレスのシールドされたバランスに追加されます。この受信者アドレスは、以前プールに登録されていたシールドアドレスである必要があります。

ログインしたときの`Recipient address`には、デフォルトでログインしたアドレスが入力されています。ツールの使い方によって、変更することができます。

新しいアカウントを設定すると、後でプールにログインしたり、トルネードのシールド残高を確認したり、シールドアドレスかシールドキーを使ってシールド送金を受け取ったりすることができるようになります。

*All information about how to use these elements to log in or where to find your shielded key are available on* [logging-in-tornado-cash-nova.md](logging-in-tornado-cash-nova.md)*.*

#### **The following deposits 💸**
次の預金は、口座がすでに設定されていることを除いて、最初の預金と同じルールに従います。

シールドアドレス/キーでプールにログインすることで、選んだ金額を選んだシールドアドレスに好きなように入金することができます。

⚠️ベータ版であるため、現在は入金が1ETH/トランザクションに制限されています。
しかし、コミュニティがこの上限を増やしたいと思った場合、1ETHの上限額はガバナンスの提案によっていつでも変更することが可能です。

## Withdrawing Process <a href="#withdrawing-process" id="withdrawing-process"></a>
![](https://i.imgur.com/qn9eJXS.gif)

ノヴァプールから資金を引き出すには、次のいずれかの方法があります。

* 0.1、0.3、0.5、1ETHの4つの金額から選択することができます。

* `Set custom`のボタンから、完全にカスタマイズされた金額を選択できます。

### Custom Option For Withdrawal <a href="#custom-option-for-withdrawal" id="custom-option-for-withdrawal"></a>
**The custom option should only be chosen with full knowledge of the following facts and in complete confidence in your actions.**

プライバシーを守るため、4つの推奨量から1つを選ぶと、引き出しが群衆に溶け込むので、強くお勧めします。

実際、選択した金額によっては、最初の資金取引と出金との間に関連性が推し量られる場合があります。

* 当初積立額と引出額は全く同じです。

* 積立額と引出額を簡単に連動させることができます。

*For instance, a deposit of 0.42 ETH can be linked to a withdrawal of exactly 0.42 ETH or two times 0.21 ETH, which might compromise anonymity. However, with a withdrawal of 0.391 ETH, privacy is better preserved as there is no obvious link between the 0.42 & 0.391 amounts.*

### Transactions through Gnosis Chain (L2) <a href="#transctions-through-gnosis-chain-l2" id="transctions-through-gnosis-chain-l2"></a>
より安価な取引のために、Gnosis Chain（旧xDAI Chain）はLayer-2として使用される。このため、メインネットからのETHとGnosis ChainからのWETHの間にブリッジが使用されています。

そのため、ブリッジに負荷をかけるスパム攻撃を防ぐため、出金額は0.05ETHより大きくなければならない。

### Bridge daily limits
トークン退出（Gnosis ChainからEthereumへのトークンのブリッジ）の日次制限が、Gnosis Chain上のいくつかのトークンに設定されています。
1日の制限の詳細については、Gnosis Chainのドキュメントをご覧ください。
https://developers.gnosischain.com/for-users/bridges/bridge-daily-limits

*Written by* [*@ayefda*](https://torn.community/u/ayefda)

