# 新規購入PC時 セットアップ (開発者向け)

## Visual Studio Code

    winget install --id Microsoft.VisualStudioCode

## Windows Sandbox

1. 設定アプリケーション：「アプリ」→「オプション機能」→「Windowsのその他の機能」→「Windowsサンドボックス」→「OK」
2. システムを再起動

※ Hyper-Vの使用にはWindows 11 Pro、Enterprise、Educationが必要。

## Hyper-V

1. 設定アプリケーション：「アプリ」→「オプション機能」→「Windowsのその他の機能」→「Hyper-V」→「OK」
2. システムを再起動

※ Hyper-Vの使用にはWindows 11 Pro、Enterprise、Educationが必要。

## Windows 10 開発環境

1. Hyper-Vマネージャー：「クイック作成…」→「Windows 10 開発環境」→「仮想マシンの作成」→「接続」→「起動」
2. 管理者権限：slmgr -rearm
3. 設定アプリケーション：「Time & Language」→「Language」→「Add a language」→「Japan」「日本語」→「Next」→「Set as my Windows desktop language」→「Install」
4. システムを再起動
5. 設定アプリケーション：「時刻と言語」→「言語」→「日本語」→「オプション」→「使用しているキーボードのレイアウト」→「OK」
6. 設定アプリケーション：「時刻と言語」→「地域」→「国または地域」→「日本」
7. 設定アプリケーション：「時刻と言語」→「日付と時刻」→「タイムゾーン」→「(UTC +09:00) 大阪、札幌、東京」

※ 仮想環境の削除後は「C:\Users\Public\Documents\Hyper-V\Virtual hard disks\」に残るディスクイメージも削除する。削除しないとディスクが消費されたままになる。

## WSL2

###### インストール方法 (管理者権限のWindows Terminalで実行)

    wsl --install -d Ubuntu
    システム再起動

###### Ubuntu初期セットアップ

    sudo apt update
    sudo apt upgrde
    sudo apt install language-pack-ja
    echo 'export LANG=ja_JP.UTF-8' >> ~/.bashrc

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

## OpenSSHサーバ セットアップ

1. 設定アプリケーション：「アプリ」→「オプション機能」→「機能を表示」→「OpenSSHサーバー」にチェック→「次へ」→「インストール」
2. システムを再起動
3. 設定ファイルを編集する。以降の操作を管理者権限のWindows Terminalで実行する。

###### 設定ファイルを編集

    copy C:\WINDOWS\SYSTEM32\OPENSSH\sshd_config_default C:\ProgramData\ssh\sshd_config
    notepad C:\ProgramData\ssh\sshd_config

###### 変更内容

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

※ 上記設定が有効になっている場合、C:\ProgramData\ssh\administrators_authorized_keysが存在し、かつ、適切なアクセス許可が設定されていないと、C:\ProgramData\ssh\administrators_authorized_keysをチェックしに行った後で公開鍵認証そのものが無効になる。$HOME/.ssh/authorized_keysよりもC:\ProgramData\ssh\administrators_authorized_keysが優先されるため、C:\ProgramData\ssh\administrators_authorized_keysのアクセス許可が不適切だと$HOME/.ssh/authorized_keysに公開鍵を配置しておいても使われない。これを回避し$HOME/.ssh/authorized_keysの公開鍵を使った公開鍵認証が有効になるようにするには、C:\ProgramData\ssh\administrators_authorized_keysを作成して適切なアクセス許可を設定するか、C:\ProgramData\ssh\administrators_authorized_keysを使わないように設定を変更する必要がある。ここでは$HOME/.ssh/authorized_keysによる公開鍵認証が使われるように、上記のように該当する行をコメントアウトする方法で設定する。

###### sshdの起動と自動起動を設定

    Start-Service sshd # sshdを起動
    Set-Service -Name sshd -StartupType 'Automatic' # Windows起動時に自動的に起動

###### 外部からのアクセス許可を確認する

    Get-NetFirewallRule -Name *ssh* # ファイウォールルールを確認

    外部からのアクセス許可ルールが存在しない、または、ブロックされているなら次のようにルールを作成する
    New-NetFirewallRule -Name  -DisplayName 'OpenSSH Server (sshd)' -Enabled True -Direction Inbound -Protocol TCP -Action Allow -LocalPort 22 # 外部からsshdへのアクセスを許可

※ Hyper-Vのゲストからホストのsshdにアクセスする場合には上記のようなファイアウォールルールは不要。

###### (sshd起動後に設定を変更した場合: sshdを再起動する)

    Restart-Service sshd # sshdを再起動

###### OpenSSHのデフォルトシェルをPowerShell 7へ変更

    New-ItemProperty -Path "HKLM:\SOFTWARE\OpenSSH" -Name DefaultShell -Value "C:\Program Files\PowerShell\7\pwsh.exe" -PropertyType String -Force

## OpenSSHクライアント

- 設定アプリケーション：「アプリ」→「オプション機能」→「機能を表示」→「OpenSSHクライアント」にチェック→「次へ」→「インストール」

###### 認証鍵の生成

    ssh-keygen
    ~/.ssh/id_rsa.pub をログインするホストの~/.ssh/authorized_keysに登録して回る

# 参考

- []()
