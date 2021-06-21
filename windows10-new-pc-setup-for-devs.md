# 新規購入PC時 セットアップ(開発者向け)

## OpenSSH

- 設定アプリケーション：「アプリ」→「アプリと機能」→「オプション機能」→「機能の追加」→「OpenSSHクライアント」→「インストール」


##### 認証鍵の生成

    ssh-keygen

## Winget

1. Microsoft Store：「アプリインストーラー」をインストール
2. [Releases · microsoft/winget-cli · GitHub](https://github.com/microsoft/winget-cli/releases)からWingetをダウンロードおよびインストール

## Windows Terminal

    winget install "Windows Terminal"

## PowerShell

    winget install Microsoft.PowerShell

## Git

    winget install Git.Git

    git config --global user.email "メールアドレス"
    git config --global user.name "ユーザ名"

## WSL2

1. 設定アプリケーション：「アプリ」→「アプリと機能」→「オプション機能」→「Windowsのそのほかの機能」→「Linux用Windowsサブシステム」と「仮想マシンプラットフォーム」にチェック→「OK」→システム再起動
2. [https://aka.ms/wsl2kernel](https://aka.ms/wsl2kernel)から「x64マシン用WSL2 Linuxカーネル更新プログラムパッケージ」をダウンロードおよびインストール
3. wsl --set-default-version 2

## Ubuntu

1. Microsoft Store：「Ubuntu 20.04 LTS」→「起動」

    sudo apt update
    sudo apt upgrde
    sudo apt install language-pack-ja
    echo 'export LANG=ja_JP.UTF-8' >> ~/.bashrc

## Visual Studio Code

    winget install "Microsoft Visual Studio Code"

## Vim

    winget install vim
