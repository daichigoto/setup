# 新規購入PC時 セットアップ (開発者向け)

## OpenSSH

- 設定アプリケーション：「アプリ」→「アプリと機能」→「オプション機能」→「機能の追加」→「OpenSSHクライアント」→「インストール」

###### 認証鍵の生成

    ssh-keygen
    ~/.ssh/id_rsa.pub をログインするホストの~/.ssh/authorized_keysに登録して回る

## Winget

1. Microsoft Store：「アプリインストーラー」をインストール
2. [Winget](https://github.com/microsoft/winget-cli/releases)をインストール

## Windows Terminal

    winget install "Windows Terminal"

1. [Cascadia Code](https://github.com/microsoft/cascadia-code/releases)をインストール
2. Windows Terminalのフォントを「Cascadia Mono PL」へ変更

## PowerShell

    winget install Microsoft.PowerShell
    
    git clone git@github.com:daichigoto/config.git
    cd config
    ./tools/install-powershell.ps1

## Git

    winget install Git.Git
    
    git config --global user.email "メールアドレス"
    git config --global user.name "ユーザ名"

## Visual Studio Code

    winget install "Microsoft Visual Studio Code"

## Vim

    winget install vim
    
    mkdir ~\.cache\vim\dein
    cd ~\.cache\vim\dein\
    Invoke-WebRequest https://raw.githubusercontent.com/Shougo/dein.vim/master/bin/installer.ps1 -OutFile installer.ps1
    ./installer.ps1 .
    del ./installer.ps1
    
    git clone git@github.com:daichigoto/config.git
    cd config
    ./tools/install-vim.ps1
    
    vim  ← プラグインインストールが完了するまでしばらく待つ

## Commands

    winget install GnuWin32.Grep
     
    PATHへ追加 - C:\Program Files (x86)\GnuWin32\bin

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

1. 設定アプリケーション：「アプリ」→「アプリと機能」→「オプション機能」→「Windowsのそのほかの機能」→「Linux用Windowsサブシステム」と「仮想マシンプラットフォーム」にチェック→「OK」→システム再起動
2. [https://aka.ms/wsl2kernel](https://aka.ms/wsl2kernel)から「x64マシン用WSL2 Linuxカーネル更新プログラムパッケージ」をダウンロードおよびインストール
3. wsl --set-default-version 2

## Ubuntu

1. Microsoft Store：「Ubuntu 20.04 LTS」→「インストール」→「起動」


###### Ubuntu初期セットアップ

    sudo apt update
    sudo apt upgrde
    sudo apt install language-pack-ja
    echo 'export LANG=ja_JP.UTF-8' >> ~/.bashrc
