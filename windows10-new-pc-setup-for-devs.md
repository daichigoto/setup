# 新規購入PC時 セットアップ (開発者向け)

## OpenSSH

- 設定アプリケーション：「アプリ」→「アプリと機能」→「オプション機能」→「機能の追加」→「OpenSSHクライアント」→「インストール」

###### 認証鍵の生成

    ssh-keygen
    ~/.ssh/id_rsa.pub をログインするホストの~/.ssh/authorized_keysに登録して回る

## Winget

1. Microsoft Store：「App Installer」をインストール
2. [Winget](https://github.com/microsoft/winget-cli/releases)をインストール

※ パッケージ管理システムとしてWingetを使用。 

## MSYS2

    winget install MSYS2
    pacman -Syu --noconfirm

- 環境変数PATHへ「C:\msys64\usr\bin」および「C:\msys64\mingw64\bin」を追加。
- 環境変数HOMEを追加。値は「C:\Users\daichi」といったようにユーザのホームディレクトリを指定。この環境変数を指定しないとC:\msys64\home\daichiなどがホームディレクトリになり使いにくい。
- 環境変数LC_CTYPEを追加。値は「ja_JP.UTF-8」。この環境変数を指定しないとvimなどが適切に日本語を使うことができない。

※ Wingetが対応していないソフトウェアについてはMSYS2を使用。

## Windows Terminal

    winget install Microsoft.WindowsTerminal

## PowerShell

    winget install Microsoft.PowerShell

Windows TerminalでインストールしたPowerShellを起動して、次の作業を実施する。
    
    git clone git@github.com:daichigoto/config.git
    cd config
    Set-ExecutionPolicy RemoteSigned -Scope CurrentUser -Force
    ./tools/install-powershell.ps1

## Windows Terminalの設定

1. 「設定」→「規定のプロファイル」→「PowerShell」→「保存」
2. 「設定」→「規定のターミナルアプリケーション」→「Windows Terminal」→「保存」
3. [Cascadia Code](https://github.com/microsoft/cascadia-code/releases)をインストール
4. Windows Terminalを再起動
5. Windows Terminalのフォントを「Cascadia Mono PL」へ変更

## Git

    pacman -S git
    
    git config --global user.email "メールアドレス"
    git config --global user.name "ユーザ名"

## Vim

    pacman -S vim
    
    mkdir ~\.cache\vim\dein
    cd ~\.cache\vim\dein\
    Invoke-WebRequest https://raw.githubusercontent.com/Shougo/dein.vim/master/bin/installer.ps1 -OutFile installer.ps1
    Set-ExecutionPolicy RemoteSigned -Scope CurrentUser -Force
    ./installer.ps1 .
    del ./installer.ps1
   
    cd ~/Documents/
    git clone git@github.com:daichigoto/config.git
    cd config
    ./tools/install-vim.ps1
    
    vim  ← プラグインインストールが完了するまでしばらく待つ

## Visual Studio Code

    winget install Microsoft.VisualStudioCode

## Windowsサンドボックス

1. 設定アプリケーション：「アプリ」→「オプション機能」→「Windowsのその他の機能」→「Windowsサンドボックス」→「OK」
2. システムを再起動

## Hyper-V

1. 設定アプリケーション：「アプリ」→「オプション機能」→「Windowsのその他の機能」→「Hyper-V」→「OK」
2. システムを再起動

## Windows 10 開発環境

1. Hyper-Vマネージャー：「クイック作成…」→「Windows 10 開発環境」→「仮想マシンの作成」→「接続」→「起動」
2. 管理者権限：slmgr -rearm
3. 設定アプリケーション：「Time & Language」→「Language」→「Add a language」→「Japan」「日本語」→「Next」→「Set as my Windows desktop language」→「Install」
4. システムを再起動
5. 設定アプリケーション：「時刻と言語」→「言語」→「日本語」→「オプション」→「使用しているキーボードのレイアウト」→「OK」
6. 設定アプリケーション：「時刻と言語」→「地域」→「国または地域」→「日本」
7. 設定アプリケーション：「時刻と言語」→「日付と時刻」→「タイムゾーン」→「(UTC +09:00) 大阪、札幌、東京」

仮想環境削除後、「C:\Users\Public\Documents\Hyper-V\Virtual hard disks\」に残るディスクイメージも削除。

## WSL2

    wsl --install -d Ubuntu
    システム再起動

###### Ubuntu初期セットアップ (Ubuntu 22.04 LTSおよびこれ以降のバージョン)

    sudo apt update
    sudo apt upgrde

###### Ubuntu初期セットアップ (Ubuntu 22.04 LTSよりも前のバージョン)

    sudo apt update
    sudo apt upgrde
    sudo apt install language-pack-ja
    echo 'export LANG=ja_JP.UTF-8' >> ~/.bashrc

# 参考

- [Windows 10搭載PCを買ったら最初にやっておきたいこと【開発者編】 \| TECH\+](https://news.mynavi.jp/article/20210622-1904714/)
