# 新規購入M1 Mac時 セットアップ (執筆環境)

## OpenSSH

- システム環境設定：「共有」→「リモートログイン」にチェック（SSH経由のログインを許可）

###### 認証鍵生成

    ssh-keygen

###### $HOME/.ssh/authorized_keys

- ~/.ssh/id_rsa.pub をログイン先ホストの ~/.ssh/authorized_keys に登録
- リモートアクセスしてくるホストの公開鍵を$HOME/.ssh/authorized_keysへ追加
- 仮想環境の公開鍵を$HOME/.ssh/authorized_keysへ追加

###### ~/.ssh/config に追加するアクセス先の設定

    Host ホスト名
            Hostname            IPアドレス
            User                ユーザ名
            IdentityFile        ~/.ssh/id_rsa
            ForwardAgent        yes

###### Github.comへ公開鍵を登録してからアクセス設定を実施

    git config --global user.email "メールアドレス"
    git config --global user.name "ユーザ名"

## Homebrew

###### インストール方法

    /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"  
    echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile  
    eval "$(/opt/homebrew/bin/brew shellenv)"

※ [Homebrew](https://brew.sh/)に掲載されている最新のインストール方法を参照すること。


## OneDrive

###### インストール方法

    brew install onedrive

## Neovim

###### インストール方法

    brew install neovim
    
    mkdir -p ~/.cache/nvim/dein
    cd ~/.cache/nvim/dein/
    curl https://raw.githubusercontent.com/Shougo/dein.vim/master/bin/installer.sh > installer.sh
    sh ./installer.sh .
    rm ./installer.sh
   
    mkdir -p ~/Documents
    cd ~/Documents/ 
    git clone git@github.com:daichigoto/config.git
    cd config
    ./tools/install-nvim.sh
    
    nvim  ← プラグインインストールが完了するまでしばらく待つ

## misc

    cd ~
    mkdir Documents
    cd Documents
    git clone git@github.com:daichigoto/misc.git
    
    echo 'export PATH="${HOME}/Documents/misc/bin:${PATH}";' >> ~/.zprofile
    source ~/.zprofile
