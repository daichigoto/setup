# OpenSSHサーバ セットアップ

1. 設定アプリケーション：「アプリ」→「オプション機能」→「機能の追加」→「OpenSSHサーバー」にチェック→「インストール」
2. 設定ファイルを編集する。管理者権限のWindows Terminal：

##### 設定ファイルを作成

    cd C:\Windows\System32\OpenSSH\
    copy sshd_config_default sshd_config

##### 設定ファイルを編集

    cd C:\Windows\System32\OpenSSH\
    notepad sshd_config

3. 管理者権限のWindows Terminal:

##### sshdを起動する方法と自動起動を設定する方法

    Start-Service sshd # sshdを起動
    Set-Service -Name sshd -StartupType 'Automatic' # Windows起動時に自動的に起動

##### ファイアウォールを設置して外部からのアクセスを許可する方法

    Get-NetFirewallRule -Name *ssh* # ファイウォールルールを確認
    New-NetFirewallRule -Name sshd -DisplayName 'OpenSSH Server (sshd)' -Enabled True -Direction Inbound -Protocol TCP -Action Allow -LocalPort 22 # 外部からsshdへのアクセスを許可

※ Hyper-Vのゲストからホストのsshdにアクセスする場合には上記ファイアウォールルールは不要。


