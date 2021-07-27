# 新規購入M1 Mac時 セットアップ (開発者向け)

## Homebrew

###### インストール方法

    /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"  
    echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile  
    eval "$(/opt/homebrew/bin/brew shellenv)"

※ [Homebrew](https://brew.sh/)に掲載されている最新のインストール方法を参照すること。

## OpenSSH

- システム環境設定：「共有」→「リモートログイン」にチェック（SSH経由のログインを許可）

###### 認証鍵生成

    ssh-keygen

###### $HOME/.ssh/authorized_keys

- ~/.ssh/id_rsa.pub をログイン先ホストの ~/.ssh/authorized_keys に登録
- リモートアクセスしてくるホストの公開鍵を$HOME/.ssh/authorized_keysへ追加

###### ~/.ssh/config に追加するアクセス先の設定

    Host ホスト名  
            Hostname            IPアドレス  
            User                ユーザ名  
            IdentityFile        ~/.ssh/id_rsa  
            ForwardAgent        yes  

###### Github.comへ公開鍵を登録してからアクセス設定を実施

    git config --global user.email "メールアドレス"  
    git config --global user.name "ユーザ名"

## Visual Studio Code

###### インストール方法

    brew install visual-studio-code

## Mac Terminal

1. [Cascadia Code](https://github.com/microsoft/cascadia-code/releases)インストール
2. ターミナル：「環境設定」→「プロファイル」→「Basic」→「テキスト」→「変更…」→「すべてのフォント」→「Cascadia Mono PL」→書体「エクストラ・ライト」→サイズ「14」

## Display Menu

1. App Store：「Display Menu」→「入手」
2. ディスプレイ調整

## AppCleaner

- [AppCleaner](https://freemacsoft.net/appcleaner/)インストール

