# 新規購入M1 Mac時 セットアップ (開発者向け)

1. App Store：「Display Menu」→「入手」
2. ディスプレイ調整
3. [AppCleaner](https://freemacsoft.net/appcleaner/)インストール
4. [Homebrew](https://brew.sh/)インストール

    /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
    echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
    eval "$(/opt/homebrew/bin/brew shellenv)"

5. システム環境設定：「共有」→「リモートログイン」にチェックを入れSSH経由のログインを許可

    ssh-keygen

##### ~/.ssh/config

Host ホスト名
	Hostname	IPアドレス
	User		ユーザ名
	IdentityFile	~/.ssh/id_rsa
	ForwardAgent	yes

6. Github.comへ公開鍵を登録

    git config --global user.email "メールアドレス"
    git config --global user.name "ユーザ名"

7. [Visual Studio Code](https://code.visualstudio.com/)インストール

    brew install visual-studio-code
