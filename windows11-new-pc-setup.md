# 新規購入PC時 セットアップ

## 事前準備

- Microsoftアカウントの用意 ([Microsoftアカウント](https://account.microsoft.com/))
- ネットワークSSIDおよびパスワード
- デバイスの名称(15字以内、A-Z_-のみ使用可)

## 初回電源ON時セットアップ

1. 電源ON
2. 「日本」→「はい」→「Microsoft IME」→「はい」→「スキップ」→ネットワーク選択→「接続」→パスワード入力→「次へ」→「次へ」→「同意」→デバイスの名前を入力→「次へ」→「個人用に設定 or 職場または学校用に設定する」→「サインイン」→Microsoftアカウント入力→(生体認証がある場合)「はい、セットアップします」→「PINの作成」→「OK」→「同意」→「スキップ」→「スキップ」

## 初回サインイン後セットアップ

1. 設定アプリケーション：「時刻と言語」→「言語と地域」→「日本語」→「言語のオプション」→「Microsoft IME」→「キーボードオプション」→「キーとタッチのカスタマイズ」→「各キー/キーの組み合わせに好みの機能を割り当てます」→「オン」→「Ctrl + Space」→「IME-オン/オフ」
2. 設定アプリケーション：「システム」→「名前の変更」→認識しやすいPCの名前を入力→「次へ」→「今すぐ再起動する」
3. Windows Update
4. ベンダアップデート
5. プレインストールアプリの調査とアンインストール（設定アプリケーション：「アプリ」→「インストールされているアプリ」）
6. スタートアップアプリの調査と無効化（設定アプリケーション：「アプリ」→「スタートアップ」）
7. スタートメニューの調査とアンインストール（C:\ProgramData\Microsoft\Windows\Start Menu\）
8. バッテリーを長寿命設定へ変更
9. 設定アプリケーション：「個人用設定」→「色」→「モードを選ぶ」→「ダーク」
10. 設定アプリケーション：「システム」→「ディスプレイ」→「夜間モード」を「オン」または「winget install --id flux.flux」でf.luxをインストール
11. 周辺機器の接続とセットアップ
12. PowerToolsをインストールして、「常に管理者として実行する」を「オン」にし、さらに、CapsLockをCtrlへ変更 (winget install --name 'PowerToys (Preview)')
13. 設定アプリケーション：「システム」→「電源＆バッテリー」→「画面とスリープ」→「電源接続時に、次の時間が経過した後にデバイスをスリープ状態にする」→「なし」、コントロールパネル：「ハードウェアとサウンド」→「電源オプション」→「カバーを閉じたときの動作の選択」→「カバーを閉じたときの動作」×「電源に接続」を「何もしない」へ変更→「変更の保存」
14. タッチパッドの設定
15. 設定アプリケーション：「Bleutoothとデバイス」→「タッチパッド」→「タップ」→「右クリックするにはタッチパッドの右下を押します」のチェックを外す
16. 設定アプリケーション：「Bleutoothとデバイス」→「タッチパッド」→「高度なジェスチャ」→「3本指ジェスチャの構成」→「上方向にスワイプ:ウィンドウの最大化、下方向にスワイプ:ウィンドウの最小化、左方向にスワイプ:ウィンドウを左にスナップする、右方向にスワイプ:ウィンドウを右にスナップする」に変更

## PowerToys設定サンプル

#### 管理者モード

- 常に管理者として実行する→「オン」

#### キーの再マップ

|変更前キー|変更後キー|
|:---|:---|
|「Caps Lock」|「Ctrl」|

#### ショートカット

|変更前キー|変更後キー|対象アプリ|
|:---|:---|:---|
|「Win」＋「Esc」|「Alt」＋「Esc」|すべてのアプリ|
|「Win」＋「0」|「Ctrl」＋「0」|すべてのアプリ|
|「Win」＋「A」|「Ctrl」＋「A」|すべてのアプリ|
|「Win」＋「C」|「Ctrl」＋「C」|すべてのアプリ|
|「Win」＋「F」|「Ctrl」＋「F」|すべてのアプリ|
|「Win」＋「N」|「Ctrl」＋「N」|すべてのアプリ|
|「Win」＋「P」|「Ctrl」＋「P」|すべてのアプリ|
|「Win」＋「Q」|「Alt」＋「F4」|すべてのアプリ|
|「Win」＋「R」|「Ctrl」＋「R」|すべてのアプリ|
|「Win」＋「S」|「Ctrl」＋「S」|すべてのアプリ|
|「Win」＋「T」|「Ctrl」＋「T」|すべてのアプリ|
|「Win」＋「V」|「Ctrl」＋「V」|すべてのアプリ|
|「Win」＋「W」|「Ctrl」＋「W」|すべてのアプリ|
|「Win」＋「Z」|「Ctrl」＋「Z」|すべてのアプリ|
|「Win」＋「=」|「Ctrl」＋「=」|すべてのアプリ|
|「Win」＋「-」|「Ctrl」＋「-」|すべてのアプリ|
|「Win」＋「Shift」＋「N」|「Ctrl」＋「Shift」＋「N」|すべてのアプリ|
|「Win」＋「Shift」＋「T」|「Ctrl」＋「Shift」＋「T」|すべてのアプリ|
|「Win」＋「Shift」＋「V」|「Ctrl」＋「Shift」＋「V」|すべてのアプリ|
|「Win」＋「Shift」＋「[」|「Ctrl」＋「Shift」＋「Tab」|すべてのアプリ|
|「Win」＋「Shift」＋「]」|「Ctrl」＋「Tab」|すべてのアプリ|
|「Win」＋「Shift」＋「N」|「Ctrl」＋「Shift」＋「P」|firefox|
|「Win」＋「V」|「Ctrl」＋「Shift」＋「V」|messenger|
|「Win」＋「V」|「Ctrl」＋「Shift」＋「V」|msedge|
|「Win」＋「R」|「Ctrl」＋「]」|photoscapex|
|「Win」＋「V」|「Ctrl」＋「Shift」＋「V」|slack|
|「Win」＋「V」|「Ctrl」＋「Shift」＋「V」|thunderbird|
|「Ctrl」＋「A」|「Home」|windowsterminal|
|「Ctrl」＋「D」|「Ctrl」＋「Delete」|windowsterminal|
|「Ctrl」＋「E」|「End」|windowsterminal|
|「Ctrl」＋「K」|「Ctrl」＋「End」|windowsterminal|
|「Win」＋「C」|「Ctrl」＋「Shift」＋「C」|windowsterminal|
|「Win」＋「N」|「Ctrl」＋「Shift」＋「N」|windowsterminal|
|「Win」＋「T」|「Ctrl」＋「Shift」＋「T」|windowsterminal|
|「Win」＋「V」|「Ctrl」＋「Shift」＋「V」|windowsterminal|
|「Win」＋「W」|「Ctrl」＋「Shift」＋「W」|windowsterminal|

# 参考

- [Windows 11搭載PCを買ったら最初にやっておきたいこと【基本編】 | TECH+](https://news.mynavi.jp/article/20211014-2083192/)
