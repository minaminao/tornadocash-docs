# Compliance Tool
設計上、ブロックチェーン上ではすべてが公開されるため、利用者のプライバシーの権利を奪う可能性があります。誰もがすべての取引履歴にアクセスすることができるのです。この問題に対処するため、Tornado Cashプロトコルは、暗号通貨保有者が自分のプライバシーを取り戻し、匿名性を獲得することを可能にします。実際、ユーザーは送信元アドレスと送信先アドレスの間のオンチェーンリンクを解除することができます。

しかし、プライバシーの維持と経済的自由の確保は、決してコンプライアンス違反を犠牲にしてまで行うべきものではありません。プライバシーの権利は、私たちが提供する情報とそれを提供する相手についてコントロールできる能力にあります。

この範囲では、**Tornado.Cash Compliance Tool enables users to prove the origin of their funds.**は各入金後に生成されたノートへの感謝、**this tool will issue a cryptographically verified proof of transactional history**は資産の入金＆引き出しに使用されるイーサリアムアドレスを使用しています。

このツールに関連するMediumの投稿では、その開発と発売について詳しく知ることができます。[**Tornado.Cash compliance Medium Post**](https://tornado-cash.medium.com/tornado-cash-compliance-9abbf254a370).

したがって、Tornado.Cashプールから引き出した保有資産の出所を証明する必要がある場合は、以下の[Compliance Tool](https://tornadocash.eth.link/compliance)を使用してください。

![https://app.tornado.cash/compliance/](../.gitbook/assets/capture-de-cran-2021-09-02-a-14.57.11.png)

## How To Use the Compliance Tool?
[Tornado.Cash app](https://tornadocash.eth.link) を通して行われた各預金で、新しい Note がプロトコルによって生成されます。このノートは、預け入れた資産を後で引き出す際に必要なものです。また、必要に応じて、ユーザーが資産の出所を証明するためのコンプライアンスレポートを作成することもできます。

*More information about how to deposit & withdraw assets on Tornado.Cash are available on:* [*Deposit & Withdraw*](deposit-withdraw.md)*.*

コンプライアンスレポートを取得するためには、入金後に作成されたメモを専用ボックスにコピーする必要があります。

### Before Withdrawal
Noteがまだ使われていない（つまり、資産がまだ引き出されていない）場合、Complianceツールは、預金に関する情報のみを提供します。

* 入金時のトランザクションハッシュ。

* 送信元アドレスです。

* コミットメントハッシュ

コミットメントは、入金のたびに生成されるバイトのハッシュ化されたランダムな領域で、取引を特徴付けるためにTornado.Cashスマートコントラクトに送信される。

![https://app.tornado.cash/compliance/](../.gitbook/assets/capture-de-cran-2021-09-02-a-15.07.01.png)

*You can find more information about how Tornado.Cash achieve to provide privacy by reading* [*How does Tornado.Cash work?*](../general/how-does-tornado.cash-work.md)*.*

### After Withdrawal
メモが使用された場合（メモを使用して所定の住所に資産が引き出された場合）、コンプライアンス・ツールは上記の情報を追加して完成させます。

* 出金時のトランザクションハッシュ。

* 宛先アドレスです。

* Nullifier Hashのことです。

nullifierハッシュは、オンチェーンに送信され、スマートコントラクトとMerkleツリーデータと照合され、引き出しが許可されるパブリックインプットです。

![https://app.tornado.cash/compliance/](../.gitbook/assets/capture-de-cran-2021-09-02-a-15.12.23.png)

そのため、Tornado.Cashで使用された資産の取引履歴を証明するために、ユーザーは送信元アドレスと送信先アドレスを再リンクすることができます。

また、この情報はPDF形式でダウンロードすることができ、希望する第三者に送付することが容易にできます。

![https://app.tornado.cash/compliance/](../.gitbook/assets/capture-de-cran-2021-09-02-a-15.12.53.png)

*Written by* [*@ayefda*](https://torn.community/u/ayefda)

