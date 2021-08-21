# WSL2 セットアップ

## Windows 10 2021年8月以降

    wsl --install -d Ubuntu

###### Ubuntu初期セットアップ

    sudo apt update
    sudo apt upgrde
    sudo apt install language-pack-ja
    echo 'export LANG=ja_JP.UTF-8' >> ~/.bashrc

## Windows 10 2021年7月以前

1. 設定アプリケーション：「アプリ」→「アプリと機能」→「オプション機能」→「Windowsのそのほかの機能」→「Linux用Windowsサブシステム」と「仮想マシンプラットフォーム」にチェック→「OK」→システム再起動
2. [https://aka.ms/wsl2kernel](https://aka.ms/wsl2kernel)から「x64マシン用WSL2 Linuxカーネル更新プログラムパッケージ」をダウンロードおよびインストール
3. wsl --set-default-version 2

###### Ubuntuインストール

1. Microsoft Store：「Ubuntu 20.04 LTS」→「インストール」→「起動」

###### Ubuntu初期セットアップ

    sudo apt update
    sudo apt upgrde
    sudo apt install language-pack-ja
    echo 'export LANG=ja_JP.UTF-8' >> ~/.bashrc

# 参考

- [Windows 10でLinuxコマンドを実行する方法 \| TECH\+](https://news.mynavi.jp/article/20210709-1915359/)
