# OpenSSHサーバ セットアップ

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

※ ユーザーがAdministratorsグループに所属している場合、上記設定が有効になっているとC:\ProgramData\ssh\administrators_authorized_keysが存在し、かつ、適切なアクセス許可が設定されていないと、C:\ProgramData\ssh\administrators_authorized_keysをチェックしに行った後で公開鍵認証そのものが無効になる。$HOME/.ssh/authorized_keysよりもC:\ProgramData\ssh\administrators_authorized_keysが優先されるため、C:\ProgramData\ssh\administrators_authorized_keysのアクセス許可が不適切だと$HOME/.ssh/authorized_keysに公開鍵を配置しておいても使われない。これを回避し$HOME/.ssh/authorized_keysの公開鍵を使った公開鍵認証が有効になるようにするには、C:\ProgramData\ssh\administrators_authorized_keysを作成して適切なアクセス許可を設定するか、C:\ProgramData\ssh\administrators_authorized_keysを使わないように設定を変更する必要がある。ここでは$HOME/.ssh/authorized_keysによる公開鍵認証が使われるように、上記のように該当する行をコメントアウトする方法で設定する。

※ 2024-05-02現在、上記方法でも公開鍵を使った認証が使えなくなっていることを確認。設定を元に戻して__PROGRAMDATA__/ssh/administrators_authorized_keysを使う方法に設定しても公開鍵を使えないことを確認。公開鍵によるログインを行うにはさらに別の設定が必要になった可能性がある。

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

# 参考

- [Windows 11搭載PCを買ったら最初にやっておきたいこと【アプリ編】 OpenSSHサーバ](https://news.mynavi.jp/article/20211020-2097210/4)
