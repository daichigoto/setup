# 新規購入PC時 セットアップ (執筆環境)

## Microsoft Edge

- 「拡張機能」→「Chrome ウェブストア」→「Create Link」→「Chrome に追加」

    Name    Format                                  Filter
    GLSD    <access ref="%url%">%title%</access>    s/&/&amp;/g
    Title   %title%                                 s/&/&amp;/g

## OpenSSHサーバ

- 設定アプリケーション：「アプリ」→「オプション機能」→「機能の追加」→「OpenSSHサーバー」にチェック→「インストール」

##### C:\ProgramData\ssh\sshd_config

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

##### sshd起動および自動起動設定

    Start-Service sshd # sshdを起動
    Set-Service -Name sshd -StartupType 'Automatic' # Windows起動時に自動的に起動

##### $HOME/.ssh/authorized_keys

    仮想環境の公開鍵を$HOME/.ssh/authorized_keysへ追加

## ユーティリティ

- [Sizer](http://www.brianapps.net/sizer/)
