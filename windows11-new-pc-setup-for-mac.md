# 新規購入PC時 セットアップ (Macユーザ向け)

## キーボードをMacへ寄せる

- [Ctrl2cap - Windows Sysinternals | Microsoft Docs](https://docs.microsoft.com/en-us/sysinternals/downloads/ctrl2cap)

###### 「Caps Lock」→「Ctrl」

    .\ctrl2cap.exe /install
    システム再起動

###### 元に戻す

    .\ctrl2cap.exe /uninstall
    システム再起動

- [PowerToys](https://docs.microsoft.com/en-us/windows/powertoys/install)

###### インストール方法

    winget install --id Microsoft.PowerToys

1. 「全般」→「常に管理者として実行する」→「オン」
2. 「全般」→「起動時に実行する」→「オン」
3. 「Keyboard Manager」→「キーの再マップ」
4. 「Keyboard Manager」→「ショートカットの再マップ」

###### キーの再マップ

|変更前キー|再マップキー|
|:---|:---|
|「Alt (Left)」|Win (Left)|

###### ショートカットキー再マップサンプル

|変更前キー|再マップショートカットキー|アプリ|主な操作|
|:---|:---|:---|:---|
|「Win」＋「C」|「Ctrl」＋「C」|すべて|コピー|
|「Win」＋「V」|「Ctrl」＋「V」|すべて|貼り付け|
|「Win」＋「A」|「Ctrl」＋「A」|すべて|全選択|
|「Win」＋「N」|「Ctrl」＋「N」|すべて|新規ウィンドウ作成|
|「Win」＋「T」|「Ctrl」＋「T」|すべて|新規タブ作成|
|「Win」＋「Q」|「Alt」＋「F4」|すべて|ウィンドウを閉じる|
|「Win」＋「W」|「Ctrl」＋「W」|すべて|タブを閉じる|
|「Win」＋「S」|「Alt」＋「S」|すべて|保存|
|「Win」＋「S」|「Ctrl」＋「S」|code|保存|
|「Win」＋「Z」|「Ctrl」＋「Z」|すべて|アンドゥ|
|「Win」＋「Shift」＋「}」|「Ctrl」＋「Tab」|すべて|タブを右へ移動|
|「Win」＋「Shift」＋「{」|「Ctrl」＋「Shift」＋「Tab」|すべて|タブを左へ移動|

###### 備考

1. Ctrl2Capは優先度が高い
2. PowerToysは優先度が低い
3. PowerToysの「キーの再マップ」は仮想環境ゲストと相性が悪い

- システム環境設定(Mac)

1. 「キーボード」→「ショートカット」→「アプリケーション」→「＋」

|アプリケーション|アクション|ショートカットキー|備考|
|:---|:---|:---|:---|
|Google Chrome|場所を開く…|^L|USキーボード向け|
|Safari|場所を開く…|^L|USキーボード向け|

###### 備考

1. 「Win」＋「L」はWindows 10ではスクリーンロック。このショートカットキーは変更が難しい。Mac側で「⌘」＋「L」を使わないようにすることでストレスを回避。

## タッチパッドをMacへ寄せる

1. 設定アプリケーション：「Bluetoothとデバイス」→「タッチパッド」→「右クリックするにはタッチパッドの右下を押します」のチェックを外す

## マウスをMacへ寄せる(Logicool Optionsの場合)

- Logicool Options：「ポイント＆スクロール」→「スクロールホイールの方向」→「反転」

## Windows-Mac間テキスト共有（ユニバーサルクリップボードもどき）

1. Google Drive

## Windows-Mac間ファイル共有（ユニバーサルクリップボードもどき）

1. OneDrive

## ユーザ辞書の移行

1. メモ帳：「エクスポートしたユーザ辞書データ(テキスト)」を開く→「ANSIで保存」
2. タスクバー：「単語の追加」→「ユーザ辞書ツール」→「ツール」→「テキストファイルから登録」

# 参考

- [Windows 10搭載PCを買ったら最初にやっておきたいこと【Macユーザー編】 \| TECH\+](https://news.mynavi.jp/article/20210712-1907494/)
