# FreeBSD新規インストール時(amd64) セットアップ (執筆環境)

## PATH

    ~/Documents/tttcmds/bin を追加
    ~/Documents/misc/bin を追加

###### sh系

    export PATH=/Documents/tttcmds/bin:~/Documents/misc/bin:$PATH

###### fish

    set -x PATH ~/Documents/tttcmds/bin ~/Documents/misc/bin $PATH

## misc

    mkdir -p ~/Documents
    cd ~/Documents/
    git clone git@github.com:daichigoto/misc.git
    cd misc
    make

## tttcmds

    sudo pkg install kyua

    mkdir -p ~/Documents
    cd ~/Documents/
    git clone git@github.com:daichigoto/tttcmds.git
    cd tttcmds
    make

## ユーティリティ

    sudo pkg install -y zip
    sudo pkg install -y gsed
    sudo pkg install -y gawk
    sudo pkg install -y nginx
    sudo pkg install -y neovim
    sudo pkg install -y fzf
    sudo pkg install -y bat

###### /usr/local/etc/nginx/nginx.conf

    --- /usr/local/etc/nginx/nginx.conf-dist        2021-07-05 00:59:41.000000000 +0900
    +++ /usr/local/etc/nginx/nginx.conf     2021-07-17 14:35:26.934724000 +0900
    @@ -1,5 +1,6 @@
    
     #user  nobody;
    +user daichi daichi;
     worker_processes  1;
    
     # This default error log path is compiled-in to make sure configuration parsing
    @@ -21,6 +22,8 @@
    
     http {
         include       mime.types;
    +    charset       UTF-8;
    +    charset_types text/plain;
         default_type  application/octet-stream;
    
         #log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
    @@ -39,15 +42,18 @@
    
         server {
             listen       80;
    -        server_name  localhost;
    +        #server_name  localhost;
    +        server_name  192.168.185.50;
    
             #charset koi8-r;
    
             #access_log  logs/host.access.log  main;
    
             location / {
    -            root   /usr/local/www/nginx;
    -            index  index.html index.htm;
    +            #root   /usr/local/www/nginx;
    +            #index  index.html index.htm;
    +            root   /Users/daichi/Documents;
    +           autoindex on;
             }
    
             #error_page  404              /404.html;

###### /usr/local/etc/nginx/mime.types

    --- /usr/local/etc/nginx/mime.types-dist        2021-07-05 00:59:41.000000000 +0900
    +++ /usr/local/etc/nginx/mime.types     2021-07-17 14:38:24.718149000 +0900
    @@ -11,6 +11,7 @@
    
         text/mathml                                      mml;
         text/plain                                       txt;
    +    text/plain                                       yd;
         text/vnd.sun.j2me.app-descriptor                 jad;
         text/vnd.wap.wml                                 wml;
         text/x-component                                 htc;

###### /etc/rc.confに追加する設定

    # nginx
    nginx_enable="YES"

###### neovim

    mkdir -p ~/.cache/nvim/dein
    cd ~/.cache/nvim/dein/
    curl https://raw.githubusercontent.com/Shougo/dein.vim/master/bin/installer.sh > installer.sh
    sh ./installer.sh .
    rm ./installer.sh

    mkdir -p ~/Documents
    cd ~/Documents/
    git clone git@github.com:daichigoto/config.git
    ./config/tools/install-nvim.sh

    nvim ← 処理が完了するまで待機
