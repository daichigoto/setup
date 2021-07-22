# 新規購入PC時 セットアップ (執筆環境)

## OpenSSHサーバ

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

###### sshd起動および自動起動設定

    Start-Service sshd # sshdを起動
    Set-Service -Name sshd -StartupType 'Automatic' # Windows起動時に自動的に起動

###### $HOME/.ssh/authorized_keys

    仮想環境の公開鍵を$HOME/.ssh/authorized_keysへ追加

###### シェルをpwshへ変更

    New-ItemProperty -Path "HKLM:\SOFTWARE\OpenSSH" -Name DefaultShell -Value "C:\Program Files\PowerShell\7\pwsh.exe" -PropertyType String -Force 

## misc

    cd ~
    mkdir Documents
    cd Documents
    git clone git@github.com:daichigoto/misc.git

- PATHへ追加 - ${HOME}/Documents/misc/bin

## wincmdserver

###### タスクスケジューラ

    タスクスケジューラ：「タスクスケジューラ（ローカル）」→「基本タスクの作成」
        名前                        wincmdserver
        トリガー                    ログオン時
        操作                        プログラムの開始
        プログラム/スクリプト       "C:\Program Files\PowerShell\7\pwsh.exe"
        引数の追加(オプション)      -WindowStyle Hidden -Command "C:\Users\daichi\Documents\misc\bin\wincmdserver.ps1"
        開始(オプション)            C:\Users\daichi

※ miscをインストールしてから作業すること。
※ wincmdserverが動作していれば、ssh経由でWindows 10にログインしていても~/.wincmdserver_cmdにコマンドを書き込むことでGUIアプリケーションなども実行することができる。

## OneDrive

###### タスクバー：「OneDrive」→「設定」→「アカウント」→「フォルダーの選択」

    [ ]フォルダーに格納されていないファイル
    [ ]デスクトップ
    [ ]ドキュメント
    [ ]個人用Vault
    [✓]画像
    　[✓]スクリーンショット

「OneDrive/画像/スクリーンショット」以外の同期を停止する。

## Microsoft Edge

- 「拡張機能」→「Chrome ウェブストア」→「Create Link」→「Chrome に追加」

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

###### Create Link設定

|Name|Format|Filter|
|:---|:---|:---|
|GSML|&lt;access ref="%url%"&gt;%title%&lt;/access&gt;|s/&amp;/&amp;amp;/g|
|Title|%title%|s/&amp;/&amp;amp;/g|

## Firefox

###### インストール

    winget install Mozilla.Firefox

- Firefox：「ツールバー」→「ツールバーをカスタマイズ」→「スクリーンショット」追加→「完了」

1. 「アドオンとテーマ」→「拡張機能」→「他のアドオンを検索」→「Format Link」→「Firefoxへ追加」
2. 「アドオンとテーマ」→「拡張機能」→「Format Link」→「オプション」

|Title|Format|
|:---|:---|
|GSML|&lt;access ref="{{url}}"&gt;{{text.s("&amp;","&amp;amp;")}}&lt;/access&gt;|
|Title|{{text.s("&amp;","&amp;amp;")}}|

## ユーティリティ

- [Sizer](http://www.brianapps.net/sizer/)
- [PhotoScape X](http://x.photoscape.org/)
- Thunderbird
- grep

###### インストール

    winget install Mozilla.Thunderbird
    winget install GnuWin32.Grep

- PATHへ追加 - C:\Program Files (x86)\GnuWin32\bin 

- Thunderbird：送信用アカウント追加
