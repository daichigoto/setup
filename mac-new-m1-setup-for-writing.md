# 新規購入M1 Mac時 セットアップ (筆

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

## Mac Terminal

1. [Cascadia Code](https://github.com/microsoft/cascadia-code/releases)インストール
2. ターミナル：「環境設定」→「プロファイル」→「Basic」→「テキスト」→「変更…」→「すべてのフォント」→「Cascadia Mono PL」→書体「エクストラ・ライト」→サイズ「14」

## Google Chrome

###### インストール方法

    brew install google-chrome

- 「その他のツール」→「拡張機能」→「Chrome ウェブストアを開きます」→「Create Link」→「Chrome に追加」 

###### Create Link設定

|Name|Format|Filter|
|:---|:---|:---|
|GSML|&lt;access ref="%url%"&gt;%title%&lt;/access&gt;|s/&amp;/&amp;amp;/g|
|Title|%title%|s/&amp;/&amp;amp;/g|
|Markdown|[%text_md%](%url%)||

###### chrome-ext

    cd ~/Documents/
    git clone git@github.com:daichigoto/chrome-ext.git

- 「その他のツール」→「拡張機能」→「デベロッパーモード」→「ON」
- 「その他のツール」→「拡張機能」→「パッケージ化されていない拡張機能を読み込む」→「書類: chrome-ext＞glsdtool」→「選択」
- 「その他のツール」→「拡張機能」→「パッケージ化されていない拡張機能を読み込む」→「書類: chrome-ext＞mncms」→「選択」
- 「その他のツール」→「拡張機能」→「パッケージ化されていない拡張機能を読み込む」→「書類: chrome-ext＞iscms」→「選択」
- アドレスバー右横：「拡張機能」→「Create Link」→「固定」
- アドレスバー右横：「拡張機能」→「GLSD Tool」→「固定を解除」
- アドレスバー右横：「拡張機能」→「Mynavi IT」→「固定を解除」
- アドレスバー右横：「拡張機能」→「Mynavi Event」→「固定を解除」

###### システム環境設定

- システム環境設定：「一般」→「デフォルトのWebブラウザ」→「Google Chrome」

## Firefox

###### インストール方法

    brew install firefox

- Firefox：「設定」→「一般」→次のフォルダーに保存する「選択…」→「デスクトップ」→「開く」
- Firefox：「ツールバー」→「ツールバーをカスタマイズ」→「スクリーンショット」追加→「完了」

1. 「アドオンとテーマ」→「拡張機能」→「他のアドオンを検索」→「Format Link」→「Firefoxへ追加」
2. 「アドオンとテーマ」→「拡張機能」→「Format Link」→「設定」

|Title|Format|HTML|
|:---|:---|:---|
|GSML|&lt;access ref="{{url}}"&gt;{{text.s("&amp;","&amp;amp;")}}&lt;/access&gt;||
|Title|{{text.s("&amp;","&amp;amp;")}}||

- Firefox：「設定」→「一般」→「カラー設定」→「背景」→「白」→「常に上書き」→「OK」

## Thunderbird

###### インストール方法

    brew install thunderbird

- 既存のメールアドレスのセットアップ：送信に使うメールアカウントを追加→「起動時にThunderbirdがデフォルトクライアントとして設定されているか確認する」からチェックを外す→「統合をスキップ」

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

## スクリーンショット

- スクリーンショット：「オプション」→保存先「デスクトップ」を選択→「フローティングサムネールを表示」のチェックを外す

## misc

    cd ~
    mkdir Documents
    cd Documents
    git clone git@github.com:daichigoto/misc.git
    
    echo 'export PATH="${HOME}/Documents/misc/bin:${PATH}";' >> ~/.zprofile
    source ~/.zprofile

## fish

    brew install fish
    echo 'fish' >> ~/.zprofile

    cd ~/Documents/ 
    cd config
    ./tools/install-fish.sh

    source ~/.zprofile
