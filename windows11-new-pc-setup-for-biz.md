# 新規購入PC時 セットアップ (ビジネスマン向け)

## VPN (Windows VPN)

- 設定アプリケーション：「ネットワークとインターネット」→「VPN」→「VPNを追加」→「保存」→「接続」

###### VPN接続ができない場合

1. ネットワーク接続：作成したVPNを選択→「プロパティ」
2. 作成したVPNのプロパティ：「セキュリティ」→「次のプロトコルを許可する」→チェック対象を変えながら接続テストを繰り返す

###### (サンプル)NTT RS-500KI VPN - 設定アプリケーション

|項目|内容|
|:---|:---|
|VPNの種類|事前共有キーを使ったL2TP/IPsec|
|事前共有キー|(定められた共有キーを入力)|
|サインイン情報の種類|ユーザー名とパスワード|
|ユーザー名|(定められたユーザ名を入力)|
|パスワード|(定められたパスワードを入力)|

###### (サンプル)NTT RS-500KI VPN - ネットワーク接続→(作成したVPN)→プロパティ→セキュリティ

|項目|項目|内容|
|:---|:---|:---|
|拡張認証プロトコル(EAP)を使う||無効化|
|次のプロトコルを許可する||有効化|
||チャレンジハンドシェイク認証プロトコル(CHAP)|有効化|
||Microsoft CHAP Version 2 (MS-CHAP v2)|有効化|

## VPN (Tailscale)

###### インストール方法

    winget install Tailscale

1. システムトレイのTailscale→「Log in...」→「Connect」

## Microsoft Office

###### インストール方法

    winget install Microsoft.Office

- 上記方法でインストールできない場合は[https://www.office.com/](https://www.office.com/)にサインインしダウンロードしてきてインストールする
- インストールしたアプリケーションのどれかひとつを起動し、Microsoft Officeが利用できるMicrosoftアカウントでサインイン

## Windowsメール

- アカウント設定
- iCloudアカウントを設定する場合、先にiCloud.comにサインインして「iCloud設定」→「Apple IDを管理」→「App用パスワード」→「＋」でアプリ用パスワードを生成し、そのパスワードを使う必要がある。

## eM Client

###### インストール方法

    winget install --id eMClient.eMClient

## Microsoft Edge

- アカウント設定

## Slack

###### インストール方法

    winget install --id SlackTechnologies.Slack

- アカウント設定。登録した電子メールアドレスで使うアカウントの分だけサインインを行う。

## LINE

###### インストール方法

    winget install --id LINE.LINE

- アカウント設定

## Facebook Messenger

###### インストール方法

    winget install --id 9WZDNCRF0083

- アカウント設定

## スタートアップ整理

- 設定アプリケーション:「アプリ」→「スタートアップ」から不要な起動時自動実行をオフにする。

# 参考

- [Windows 11搭載PCを買ったら最初にやっておきたいこと【アプリ編】 | TECH+](https://news.mynavi.jp/article/20211020-2097210/)
