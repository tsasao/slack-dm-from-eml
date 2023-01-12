# slack-dm-from-eml

## これは何?

メールはほとんど使わない、というチームでも、SaaSのアカウントを作成する際などに確認メールを受信する必要があって、
とはいえ、そのためだけにメールのサービスをセットアップするのは手間もお金もかかる。

という場合に、Slackのメンバーであれば、[メールをSlackで受信する](https://slack.com/intl/ja-jp/help/articles/206819278-Slack-%E3%81%AB%E3%83%A1%E3%83%BC%E3%83%AB%E3%82%92%E9%80%81%E4%BF%A1%E3%81%99%E3%82%8B#h_01F4WDZG8RTCTNAMR4KJ7D419V)機能が便利です。

が、メンバーでない場合は、この機能は使えない... メンバーでない場合の方が、この機能のニーズがあるのに!

ということで、slack-dm-from-emlは、メールを受け取ってSlack DMに転送します。`.forward`が使えるメールサーバを想定しています。

```
|　./slack-dm-from-eml U00000000
```


## 準備

[ここ](https://api.slack.com/apps)から、新規でSlackアプリを作ります。
名前は何でもいいのですが、ここではmail-botとします。
OAuth & PermissionsのページでBot Token Scopesに以下を追加します。
- chat:write
- mpim:write

Install to Workspaceボタンを押して、登録します。

`xoxb-` ではじまるBot User OAuth Tokenを控えておきます。

Slackのゲストは、そのゲストが参加しているチャンネルに参加しているユーザとだけDMができる仕様ですので、
適当なチャンネルのIntegrationsタブ内Appsパネルから、Add appsをクリックし、mail-botを追加します。
（メンバーの場合は、この作業は不要です。）

また、送信したいユーザのIDを調べておきます。
Slackでユーザを選んでProfileを表示させた状態で、︙内にあるCopy member IDで取得できるUではじまる文字です。
