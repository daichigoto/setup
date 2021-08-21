# OpenSSHサーバ セットアップ

1. 設定アプリケーション：「アプリ」→「オプション機能」→「機能の追加」→「OpenSSHサーバー」にチェック→「インストール」
2. 設定ファイルを編集する。管理者権限のWindows Terminal：

###### 設定ファイルを編集

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

3. sshdの起動および自動起動設定を行う。管理者権限のWindows Terminal:

###### sshdを起動する方法と自動起動を設定する方法

    Start-Service sshd # sshdを起動
    Set-Service -Name sshd -StartupType 'Automatic' # Windows起動時に自動的に起動

###### sshdを再起動する方法

    Restart-Service sshd # sshdを再起動

###### ファイアウォールを設置して外部からのアクセスを許可する方法

    Get-NetFirewallRule -Name *ssh* # ファイウォールルールを確認
    New-NetFirewallRule -Name sshd -DisplayName 'OpenSSH Server (sshd)' -Enabled True -Direction Inbound -Protocol TCP -Action Allow -LocalPort 22 # 外部からsshdへのアクセスを許可

※ Hyper-Vのゲストからホストのsshdにアクセスする場合には上記ファイアウォールルールは不要。

4. ユーザのデフォルトシェルをcmdからpwshへ変更する。

###### OpenSSHのデフォルトシェルをpwshへ変更

    New-ItemProperty -Path "HKLM:\SOFTWARE\OpenSSH" -Name DefaultShell -Value "C:\Program Files\PowerShell\7\pwsh.exe" -PropertyType String -Force
