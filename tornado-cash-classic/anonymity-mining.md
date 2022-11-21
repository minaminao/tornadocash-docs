# Anonymity Mining
アノニマスマイニングは、コインジョインやコインミキシングプロトコルのプライバシーレベルを向上させるインセンティブであり、参加者がプールで資産をヘッジした時間に応じてアノニマスポイント（AP）を報酬として与えるものである。

{ヒント スタイル="警告" %}。
*Tornado Cash anonymity mining program began on December 18, 2020 and has ended on December 18, 2021.*
{エンドヒント｝

個人は、サポートされている匿名プール（ETH、WBTC、DAI、またはcDAI）のいずれかに入金し、ブロックごとに一定量のAPを報酬として受け取ることができ、その預金がプールに残っている期間。これらのポイントは、請求されるとTORNに交換することができます。

### Anonymity points (AP)
*Readers should be aware some lower denomination deposits at the time of writing, do not produce a positive return due to the gas costs required to withdraw, redeem and exchange anonymity points*

コミュニティメンバーの一人が[a mining spreadsheet 13](https://torn.community/t/anonymity-mining-spreadsheet/720)のリソースを作成し、報酬請求に必要な手数料を見積もることで、各プールとその中に設定された各宗派の年利率（APY）を計算するのに役立っています。**It is highly recommended to view this resource and plan one’s course of action before expecting to earn yield.** スプレッドシートの下部で、関連するタブを選択すると、各プールを表示できます。

### How to earn AP
1\.入金する金額と資産をドロップダウンメニューから選択し、「接続」→「入金」をクリックします。

![](../.gitbook/assets/m3fh0gl.png)

2\.預けたメモを記録し、安全にバックアップをとってください **do not share this with anyone or risk losing your deposit and reward.**

![](../.gitbook/assets/vhustru.png)

3\.証明書を作成し、トランザクションを送信します。

4\.預金はページ下部に表示され、ここでAPの獲得量を確認できます。

![](../.gitbook/assets/k6juetp.png)

*Notes that are active (not withdrawn) are known as “unspent” notes.*

### How to claim AP
1\.まず、マイニングアカウントを作成し、簡単に回復できるようにこれらの認証情報をオンチェーンに保存する必要があります（トランザクションが必要）、**like depositing notes, you should never share your mining recovery key with anyone**と安全な場所にバックアップすることを確認してください。この機能はハードウェアウォレットではサポートされていないため、present_.indexとして保存することが推奨されます。

![](../.gitbook/assets/lskzkgk.png)

2\.未使用のノートを提供することでアクティブな預金を取り、好みのアドレスに引き出し、リレイヤーを使用するかどうか決定します（*to maintain a deposit’s anonymity it is always advised to use a relayer*）、これはノートを「使用済み」状態にします。

![](../.gitbook/assets/aid86cj.png)

**Remember to still keep your depositing notes a secret even after withdrawing, as they still retain the ability to redeem AP.**

![](../.gitbook/assets/bpsqxxr.png)

3\.アプリケーションのマイニングルートにアクセスし、使用済みノートを入力すると、次のような状況に直面することがあります。

* **The ability to claim your spent note**：「報酬を請求する」ボタンをクリックし、リレイヤーを使用するかどうかにかかわらず、トランザクションを送信してください。

![](../.gitbook/assets/e9jyqhu.png)

* **The inability to claim a spent note:** *“Warning: The note is not yet ready for anonymity mining. You can wait few days before trying again”* - これはMerkleツリーが同期しておらず、更新するためのトランザクションが必要であることを意味します。

![](../.gitbook/assets/i6qtr0f.png)

ツリーの更新には、高額な費用がかかる場合があります**it is recommended that users with small deposits wait for the larger miners to update the trees, this could take anywhere from a few days to a week**。現在の保留中のバッチと相対的にイベントを表示したい場合。*“Show mining note information”*のハイパーリンクをクリックしてください。ここで、「ツリーの更新」ボタンを通じて、引き出しに関連するツリーを同期させるために取引手数料を支払うこともできます。

![](../.gitbook/assets/d8dmxjj.png)

### How to exchange AP
1\.マイニングページの「Swap」タブに移動します。このタブは、ページの上部から2番目のナビゲーションバーからアクセスできます。

![](../.gitbook/assets/ahrjxbq.png)

2\.交換を希望するAPの量を入力するか、有効な残高を変換する場合は「最大」を選択します。この入力の下に、現在のAP/TORNレートと報酬の出力に関する情報が表示されます。報酬を受け取りたい住所を入力し、証明書を作成し、リレイヤーを通してトランザクションを送信するかどうかで確定してください。

![](../.gitbook/assets/wo55lao.png)

3\.全ての手順が正しく行われた場合、TORNは本項2.で指定された希望するアドレスに転送されます。

### Closing remarks
おめでとうございます！あなたはアノニマスマイニングに参加することに成功しました。

アノニマスセットのいずれかを採掘することを決定する際には、常に計画を立てることをお勧めします。ユーザーは、[AP/TORN rate](https://duneanalytics.com/luckyallocator/Daily-AP-TORN-Rate-v2)が需要と供給、したがって**the more people that claim the higher the rate becomes, and the less people that claim the lower it becomes**に依存していることも認識しておく必要があります。

アノニマスマイニングの詳細については、以下のリソースを参照してください。

* [Tornado.Cash governance proposal article](https://tornado-cash.medium.com/tornado-cash-governance-proposal-a55c5c7d0703)

* [Tornado.Cash anonymity mining optimisation article](https://tornado-cash.medium.com/gas-price-claimed-anonymity-mining-a-victim-but-now-everyone-can-claim-ap-5441aaa32a1a)

* [Anonymity mining explained (technical)](https://torn.community/t/anonymity-mining-technical-overview/15)

x00 x02 x03 x05 x06

*Written by* [***@xgozzy***](https://torn.community/u/xgozzy/summary)

