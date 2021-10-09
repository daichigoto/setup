# 新規購入PC時 セットアップ (開発者向け)

## MSYS2

Linux系コマンドをMSYS2経由でインストールして使用する。

###### 事前に環境変数を設定

- 環境変数PATHへ「C:\msys64\usr\bin」および「C:\msys64\mingw64\bin」を追加。Windows Terminalで「echo $env:Path」と実行し、環境変数Pathに反映されていることを確認。反映されていない場合にはシステムを再起動してから、もう一度確認する。
- 環境変数HOMEを追加。値は「C:\Users\daichi」といったようにユーザのホームディレクトリを指定。この環境変数を指定しないとC:\msys64\home\daichiなどがホームディレクトリになり使いにくい。
- 環境変数LC_CTYPEを追加。値は「ja_JP.UTF-8」。この環境変数を指定しないとvimなどが適切に日本語を使うことができない。

###### インストール方法

    winget install --id msys2.msys2
    pacman -Syu

## Git

    pacman -S git
    
    git config --global user.email "メールアドレス"
    git config --global user.name "ユーザ名"

## Vim

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

## NeoVim

###### インストール方法

1. [Home - Neovim](http://neovim.io/)からNeovimをインストール。zipファイルを展開し、C:\Users\daichi\Documents\neovim\へデプロイする。
2. C:\Users\daichi\Documents\neovim\binを環境変数Pathへ追加する。
3. Windows Terminalの再起動またはシステムを再起動し、「echo $env:Path」を実行して環境変数PathにC:\Users\daichi\Documents\neovim\binが追加されていることを確認する。

###### セットアップ方法

    mkdir ~\.cache\nvim\dein
    cd ~\.cache\nvim\dein\
    Invoke-WebRequest https://raw.githubusercontent.com/Shougo/dein.vim/master/bin/installer.ps1 -OutFile installer.ps1
    ./installer.ps1 .
    del ./installer.ps1
   
    cd ~/Documents/
    git clone git@github.com:daichigoto/config.git
    cd config
    ./tools/install-nvim.ps1
    
    nvim  ← プラグインインストールが完了するまでしばらく待つ

## PowerShell

    winget install --id Microsoft.PowerShell
    
    git clone git@github.com:daichigoto/config.git
    cd config
    ./tools/install-powershell.ps1

## Windows Terminal

1. 「設定」→「規定のプロファイル」→「PowerShell」→「保存」
2. [Cascadia Code](https://github.com/microsoft/cascadia-code/releases)をインストール
3. 「設定」→「プロファイル」→「PowerShell」→「外観」→「フォントフェイス」→「Cascadia Mono PL」→「保存」

## Visual Studio Code

    winget install --id Microsoft.VisualStudioCode

## OpenSSHサーバ


## OpenSSHクライアント

- 設定アプリケーション：「アプリ」→「アプリと機能」→「オプション機能」→「機能を表示」→「OpenSSHクライアント」にチェック→「インストール」

###### 認証鍵の生成

    ssh-keygen
    ~/.ssh/id_rsa.pub をログインするホストの~/.ssh/authorized_keysに登録して回る

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

###### Ubuntu初期セットアップ

    sudo apt update
    sudo apt upgrde
    sudo apt install language-pack-ja
    echo 'export LANG=ja_JP.UTF-8' >> ~/.bashrc

# 参考

- []()
