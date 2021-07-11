# FreeBSD新規インストール時 セットアップ

## /etc/rc.conf

    # server
    hostname="virt.ongs.co.jp"
    ifconfig_hn0="DHCP"
    
    # sshd
    sshd_enable="YES"
    sshd_flags="-oUseDNS=no -oUsePAM=no -oPermitRootLogin=no -oChallengeResponseAuthentication=no -oPasswordAuthentication=no"

    # nginx
    nginx_enable="YES"

## ssh

    ssh-keygen
    ~/.ssh/authorized_keys にログイン元ホストの公開鍵登録
    ~/.ssh/id_rsa.pub をログイン先ホストの ~/.ssh/authorized_keys に登録

## ユーティリティインストール

    pkg install -y sudo
    pkg install -y git
    pkg install -y neovim
    pkg install -y fish
    pkg install -y nginx
    pkg install -y tree
    pkg install -y bat

##### /usr/local/etc/sudoers

    --- /usr/local/etc/sudoers.dist 2021-07-01 16:07:41.000000000 +0900
    +++ /usr/local/etc/sudoers      2021-07-11 16:01:17.151297000 +0900
    @@ -91,6 +91,7 @@
    
     ## Same thing without a password
     # %wheel ALL=(ALL) NOPASSWD: ALL
    +daichi ALL=(ALL) NOPASSWD: ALL
    
     ## Uncomment to allow members of group sudo to execute any command
     # %sudo        ALL=(ALL) ALL

##### git

    git config --global user.email "メールアドレス"
    git config --global user.name "ユーザ名"

##### neovim

    git clone https://github.com/daichigoto/config
    ./config/tools/install-nvim.sh

    mkdir -p ~/.cache/nvim/dein
    cd ~/.cache/nvim/dein/
    curl https://raw.githubusercontent.com/Shougo/dein.vim/master/bin/installer.sh > installer.sh
    sh ./installer.sh .
    rm ./installer.sh

    nvim

##### fish

    sudo pw usermod daichi -s /usr/local/bin/fish
    git clone https://github.com/daichigoto/config
    ./config/tools/install-fish.sh
