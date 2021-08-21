# 新規購入PC時 セットアップ (執筆環境)

<!-- ---------------------------------------------------------------------
 リモートシステム・セットアップ
 --------------------------------------------------------------------- -->
## リモートログインシステム・セットアップ

### OpenSSHサーバ

- 設定アプリケーション：「アプリ」→「オプション機能」→「機能の追加」→「OpenSSHサーバー」にチェック→「インストール」

###### C:\ProgramData\ssh\sshd_config

    C:\ProgramData\ssh>fc /n C:\Windows\System32\OpenSSH\sshd_config_default C:\ProgramData\ssh\sshd_config
    Comparing files C:\WINDOWS\SYSTEM32\OPENSSH\sshd_config_default and C:\PROGRAMDATA\SSH\SSHD_CONFIG
    ***** C:\WINDOWS\SYSTEM32\OPENSSH\sshd_config_default
       86:
       87:  Match Group administrators
       88:         AuthorizedKeysFile __PROGRAMDATA__/ssh/administrators_authorized_keys
    ***** C:\PROGRAMDATA\SSH\SSHD_CONFIG
       86:
       87:  #Match Group administrators
       88:  #       AuthorizedKeysFile __PROGRAMDATA__/ssh/administrators_authorized_keys
    *****

※ 上記設定が有効になっている場合、C:\ProgramData\ssh\administrators_authorized_keysが存在し、かつ、適切なアクセス許可が設定されていないと、C:\ProgramData\ssh\administrators_authorized_keysをチェックしに行った後で公開鍵認証そのものが無効になる。$HOME/.ssh/authorized_keysよりもC:\ProgramData\ssh\administrators_authorized_keysが優先されるため、C:\ProgramData\ssh\administrators_authorized_keysのアクセス許可が不適切だと$HOME/.ssh/authorized_keysに公開鍵を配置しておいても使われない。これを回避し$HOME/.ssh/authorized_keysの公開鍵を使った公開鍵認証が有効になるようにするには、C:\ProgramData\ssh\administrators_authorized_keysを作成して適切なアクセス許可を設定するか、C:\ProgramData\ssh\administrators_authorized_keysを使わないように設定を変更する必要がある。ここでは$HOME/.ssh/authorized_keysによる公開鍵認証が使われるように、上記のように該当する行をコメントアウトする方法で設定する。

###### sshd起動および自動起動設定

    Start-Service sshd # sshdを起動
    Set-Service -Name sshd -StartupType 'Automatic' # Windows起動時に自動的に起動

###### シェルをpwshへ変更

    New-ItemProperty -Path "HKLM:\SOFTWARE\OpenSSH" -Name DefaultShell -Value "C:\Program Files\PowerShell\7\pwsh.exe" -PropertyType String -Force 

###### $HOME/.ssh/authorized_keys

- リモートアクセスしてくるホストの公開鍵を$HOME/.ssh/authorized_keysへ追加。
- 仮想環境の公開鍵を$HOME/.ssh/authorized_keysへ追加。

### OpenSSHクライアント

- 設定アプリケーション：「アプリ」→「アプリと機能」→「オプション機能」→「機能の追加」→「OpenSSHクライアント」→「インストール」

###### 認証鍵の生成

    ssh-keygen

- ~/.ssh/id_rsa.pub をログイン先ホストの ~/.ssh/authorized_keys に登録して回る


<!-- ---------------------------------------------------------------------
 ビルドシステム・セットアップ
 --------------------------------------------------------------------- -->
## ビルドシステム・セットアップ

## Winget

1. Microsoft Store：「App Installer」をインストール
2. [Winget](https://github.com/microsoft/winget-cli/releases)をインストール

※ パッケージ管理システムとしてWingetを使用。 

## MSYS2

    winget install MSYS2
    pacman -Syu

- 環境変数PATHへ「C:\msys64\usr\bin」および「C:\msys64\clang64\bin」を追加。ただし、${HOME}/Documents/misc/binよりも後のパスとして追加すること。${HOME}/Documents/misc/bin/make.ps1がC:\msys64\usr\bin\make.exeよりも先に実行される必要がある。
- 環境変数HOMEを追加。値は「C:\Users\daichi」といったようにユーザのホームディレクトリを指定。この環境変数を指定しないとC:\msys64\home\daichiなどがホームディレクトリになり使いにくい。
- 環境変数LC_CTYPEを追加。値は「ja_JP.UTF-8」。この環境変数を指定しないとvimなどが適切に日本語を使うことができない。

※ Wingetが対応していないソフトウェアについてはMSYS2を使用。

### misc

    cd ~
    mkdir Documents
    cd Documents
    git clone git@github.com:daichigoto/misc.git

- 環境変数PATHへ「${HOME}/Documents/misc/bin」を追加。${HOME}/Documents/misc/binは優先順位最上位で追加すること。

###### ビルドおよびインストール方法

    cd misc
    make

### tttcmds

    cd ~
    mkdir Documents
    cd Documents
    git clone git@github.com:daichigoto/tttcmds.git
    cd tttcmds
    make

- 環境変数PATHへ「${HOME}/Documents/tttcmds/bin」を追加。

<!-- ---------------------------------------------------------------------
 執筆ツール・セットアップ
 --------------------------------------------------------------------- -->
## 執筆ツール・セットアップ

### Vim

###### インストール

    pacman -S vim
     
    mkdir ~\.cache\vim\dein
    cd ~\.cache\vim\dein\
    Invoke-WebRequest https://raw.githubusercontent.com/Shougo/dein.vim/master/bin/installer.ps1 -OutFile installer.ps1
    ./installer.ps1 .
    del ./installer.ps1
     
    cd ~/Documents/
    git clone git@github.com:daichigoto/config.git
    cd config
    ./tools/install-vim.ps1
    
    vim  ← プラグインインストールが完了するまでしばらく待つ

### Google日本語入力

###### インストール

    winget install Google.JapaneseIME

- 「プロパティ」→「一般」→キー設定の選択「MS-IME」→「編集」→エントリーを追加→「OK」→「OK」

|モード|入力キー|コマンド|
|:---|:---|:---|
|変換前入力中|Ctrl Space|IMEを無効化|
|変換中|Ctrl Space|IMEを無効化|
|直接入力|Ctrl Space|IMEを有効化|
|入力文字なし|Ctrl Space|IMEを無効化|

※ キー変更が反映されるのは個々のアプリケーション再起動後。

- 「辞書ツール」→「管理」→「Microsoft IMEの日本語辞書をインポート」
- 「辞書ツール」→辞書を編集

### OneDrive

###### タスクバー：「OneDrive」→「設定」→「アカウント」→「フォルダーの選択」

    [ ]フォルダーに格納されていないファイル
    [ ]デスクトップ
    [ ]ドキュメント
    [ ]個人用Vault
    [✓]画像
    　[✓]スクリーンショット

「OneDrive/画像/スクリーンショット」以外の同期を停止する。

### Microsoft Edge

- 「拡張機能」→「Chrome ウェブストア」→「Create Link」→「Chrome に追加」

###### Create Link設定

|Name|Format|Filter|
|:---|:---|:---|
|GSML|&lt;access ref="%url%"&gt;%title%&lt;/access&gt;|s/&amp;/&amp;amp;/g|
|Title|%title%|s/&amp;/&amp;amp;/g|
|Markdown|&#091;%text_md%&#093;(%url%)||

###### chrome-ext

    cd ~/Documents/
    git clone git@github.com:daichigoto/chrome-ext.git

- 「拡張機能」→「開発者モード」→「ON」
- 「拡張機能」→「展開して読み込み」→「C:\Documents\chrome-ext\glsdtool」→「フォルダーの選択」
- 「拡張機能」→「展開して読み込み」→「C:\Documents\chrome-ext\mncms」→「フォルダーの選択」
- 「拡張機能」→「展開して読み込み」→「C:\Documents\chrome-ext\iscms」→「フォルダーの選択」
- アドレスバー右横：「glsdtool」→「メニューへ移動」
- アドレスバー右横：「mncms」→「メニューへ移動」
- アドレスバー右横：「iscms」→「メニューへ移動」

### Firefox

###### インストール

    winget install Mozilla.Firefox

- Firefox：「設定」→「一般」→次のフォルダーに保存する「参照」→「デスクトップ」→「フォルダーの選択」
- Firefox：「ツールバー」→「ツールバーをカスタマイズ」→「スクリーンショット」追加→「完了」

1. 「アドオンとテーマ」→「拡張機能」→「他のアドオンを検索」→「Format Link」→「Firefoxへ追加」
2. 「アドオンとテーマ」→「拡張機能」→「Format Link」→「オプション」

|Title|Format|HTML|
|:---|:---|:---|
|GSML|&lt;access ref="{{url}}"&gt;{{text.s("&amp;","&amp;amp;")}}&lt;/access&gt;||
|Title|{{text.s("&amp;","&amp;amp;")}}||

### Thunderbird

###### インストール

    winget install Mozilla.Thunderbird

- Thunderbird：送信用アカウント追加

### PhotoScape X

- [PhotoScape X](http://x.photoscape.org/)


<!-- ---------------------------------------------------------------------
 仮想環境-To-Windows 連携システム・セットアップ
 --------------------------------------------------------------------- -->
## 仮想環境-To-Windows 連携システム・セットアップ

### wincmdserver

- タスクスケジューラ：「タスクスケジューラ（ローカル）」→「基本タスクの作成」

###### タスクスケジューラ基本タスクの作成内容　

|項目|内容|
|:---|:---|
|名前|wincmdserver|
|トリガー|ログオン時|
|操作|プログラムの開始|
|プログラム/スクリプト|"C:\Program Files\PowerShell\7\pwsh.exe"|
|引数の追加(オプション)|-WindowStyle Hidden -Command "C:\Users\daichi\Documents\misc\bin\wincmdserver.ps1"|
|開始(オプション)|C:\Users\daichi|

- タスクスケジューラ：「タスクスケジューラ(ローカル)」→「タスクスケジューラライブラリ」→「wincmdserver」→「プロパティ」

###### wincmdserverのプロパティ

|タブ|内容|変更|
|:---|:---|:---|
|条件|コンピュータをAC電源で使用している場合のみタスクを開始する|チェックを外して無効化|
|条件|コンピュータの電源をバッテリに切り替える場合は停止する|チェックを外して無効化|
|設定|タスクを停止するまでの時間|チェックを外して無効化|

※ miscをインストールしてから作業すること。  
※ wincmdserverが動作していれば、ssh経由でWindows 10にログインしていても~/.wincmdserver_cmdにコマンドを書き込むことでGUIアプリケーションなども実行することができる。  
