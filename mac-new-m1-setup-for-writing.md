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


