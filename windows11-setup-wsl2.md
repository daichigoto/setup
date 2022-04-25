# WSL2 セットアップ

###### インストール方法(管理者権限のWindows Terminalで実行)

    wsl --install -d Ubuntu

###### Ubuntu初期セットアップ (Ubuntu 22.04 LTSおよびこれ以降のバージョン)

    sudo apt update
    sudo apt upgrde

###### Ubuntu初期セットアップ (Ubuntu 22.04 LTSよりも前のバージョン)

    sudo apt update
    sudo apt upgrde
    sudo apt install language-pack-ja
    echo 'export LANG=ja_JP.UTF-8' >> ~/.bashrc

# 参考

- [Windows 11でLinuxアプリケーション、コマンドを実行する方法 \| TECH\+](https://news.mynavi.jp/article/20210723-1915331/)
