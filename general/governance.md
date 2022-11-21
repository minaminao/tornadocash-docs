# Governance
以下のガバナンスルールは、すべての Tornado Cash プール（Tornado Cash Nova を含む）に適用されます。

### How to suggest a proposal ?
Tornado.Cashのガバナンスに参加するためには、ユーザーはまずガバナンス契約にトークンをロックする必要があります。ユーザーが投票または提案を作成した場合、提案実行期間（提案作成から8.25日）が終了するまでは、トークンのロックを解除することができません。また、ロックされたトークンは、別のアドレスに委譲することができます。

プロポーザルを作成するには、ユーザーは最低でも`1,000 TORN`を持っている必要があります。すべての提案は、[governance contract ](https://etherscan.io/address/0x5efda50f22d34F262c29268506C5Fa42cB56A1Ce)(`delegatecall`を使用)から実行される検証済みのコードを持つスマートコントラクトでなければなりません。こうすることで、ガバナンスの変更を監査し、テストすることが容易になります。

提案の投票期間は5日間です。提案は、単純多数決で総投票数が`25,000 TORN`票以上あれば成功します（投票数が少なすぎる場合、提案は自動的に失敗します）。

提案に成功すると、2日間のタイムロックがかかります。タイムロック後は、誰でもその提案を実行することができます（変更を開始することができます）。その後、3日間実行されないと、その提案は*expired*とみなされ、実行できなくなります。

これらの初期パラメータはすべて、初期には多くのTORNトークンが流通しないため、比較的小さいものです。しかし、流通する供給量が増えるにつれて、ガバナンスはこれらの閾値を調整する可能性があります。

提案の内容は以下の通りです。

* プロキシに新しいTornado Cashプールを追加する

* APリワードのレートパラメーターの変更

* TORNトークンの一時停止解除/一時停止

* `TornadoTrees`コントラクトなど、一部のコアマイニングコントラクトの変更

* 上記すべての組み合わせ

その他にも多くのことが可能です。プロトコルのガバナンスによって何が変えられるかを正確に知るには、スマートコントラクトの中で`onlyGovernance`という修飾子を持つ関数を探せばいい。

ガバナンス機能は、[this architecture diagram.](https://viewer.diagrams.net/?highlight=0000ff&edit=_blank&layers=1&nav=1&title=tornado-cash-contract-overview.drawio#Uhttps%3A%2F%2Fraw.githubusercontent.com%2FRezan-vm%2Ftornado-cash-edu%2Fmain%2Ftornado-cash-contract-overview.drawio)の赤い矢印で表されている

注：この記事の一部は[this medium post.](https://tornado-cash.medium.com/tornado-cash-governance-proposal-a55c5c7d0703)から引用しています。

### How to vote ?
まず、TORNトークンをガバナンスコントラクトに預ける（ロックする）必要があります。

に行ってください。[https://tornadocash.eth.link/governance](https://tornadocash.eth.link/governance)

`Manage`→`Lock Tab`をクリック

`Approve`ボタンをクリックして、TORNトークンを送金するためのガバナンス契約を承認してください。承認が確認されたら、入金する金額を選んで`Lock`をクリックします。ウォレットで取引を確認し、確認を待ちます。

![](<../.gitbook/assets/c05e5a1813edad280544b627b24002dc8d5adcf2 (1).png>)

投票の前に、次の重要なステップは、提案を確認することです。
正当な提案は、[Torn.community ](https://torn.community) の「提案」カテゴリに専用の投稿をする必要があります。フォーラムの投稿は、その提案に関する追加の文脈と議論を提供します。そのスレッドを読んで、その問題について自分自身の考えをまとめてください。

一度提出されたプロポーザルは、上に表示されるはずです。
[https://tornadocash.eth.link/governance](https://tornadocash.eth.link/governance)
プロポーザルは、システムに変更を加えるスマートコントラクトという形で実装されます。したがって、スマートコントラクトのアドレスを確認し、そのコードを確認することが重要です。プロポーザル契約のアドレスはこちらでご確認ください。

![](../.gitbook/assets/181d612b6c57964bab59c8e5b766f5247211083d.png)

Etherscanでコントラクトアドレスを探し、ソースコードが検証され、読み取れることを確認する。

![](../.gitbook/assets/d2d37d169a94f09156e76fa522b7974cb7c9ac3f.png)

ソースコードを読み、フォーラムの投稿に記載されている内容と一致していることを確認してください。

技術的な知識がない、または Solidity のコードを読むのに抵抗がある場合は、信頼できる人に契約書を確認してもらいましょう。

プロポーザルコードに賛成（または反対）なら、投票の時間です。

提案には5日間の投票期間があります。つまり、投票定足数である25k TORNに達するまで5日間あります。

重要投票すると、提案が提出された時点（5日間の投票期間の開始）から8.25日間、あなたのトークンはロックされます。8.25日を過ぎると、ガバナンス契約からトークンを引き出すことができます。なお、同時に2つの提案に投票してもロック期間は延長されません（8.25日のロック期間中は直近に提出された提案のみが問題となります）。

投票するには、緑色のチェックマークか赤い十字をクリックするだけです。メタマスクで取引内容を確認し、投票完了です。

### How to delegate the vote ?
トルントークンホルダーであれば、トークンを送ることなく、議決権を他人に委任することができます。

重要：トークンを委任し、委任者が投票または提案を開始した場合、委任者が投票した提案が始まった時点から8.25日間、トークンがロックされます。なお、委任はいつでも解除することができます。

デレゲーション実現のために、行ってください。[https://tornadocash.eth.link/governance](https://tornadocash.eth.link/governance)

まず、トークンをガバナンスコントラクトにロックする必要があります。**`Manage`**→**`Lock`**タブをクリック

**`Approve`**ボタンをクリックして、TORNトークンを譲渡するためのガバナンス契約を承認してください。承認が確認できたら、委任したい金額を選び、**`Lock`**をクリックします。ウォレットでトランザクションを確認し、確認を待ちます。

![](../.gitbook/assets/c05e5a1813edad280544b627b24002dc8d5adcf2.png)

最後のステップ、それは実際の委任を行うことです。再び[https://tornadocash.eth.link/governance](https://tornadocash.eth.link/governance)へ

**`Manage`**」→「**`Delegate`**」タブをクリック

委任するアドレスを記入し、**`Delegate`**をクリックします。ウォレットで取引を承認し、確認を待ちます。

![](../.gitbook/assets/43c05d176d7f75a336af7a865565c9b23786b98c.png)

ロックされた残高の総量が委譲されます。

いつでも委任を解除することができます。`Manage`→`Undelegate`タブの`Undelegate`ボタンを押すだけで、委任を解除することができます。

*Written by* [*@rezan*](https://torn.community/u/Rezan/summary)

*Updated by* [*@bt11ba*](https://torn.community/u/bt11ba/)

