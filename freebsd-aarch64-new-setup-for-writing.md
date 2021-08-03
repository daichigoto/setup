# FreeBSD新規インストール時(aarch64) セットアップ (執筆環境)

## PATH

    ~/Documents/tttcmds/bin を追加
    ~/Documents/misc/bin を追加

###### sh系

    export PATH=/Documents/tttcmds/bin:~/Documents/misc/bin:$PATH

###### fish

    set -x PATH ~/Documents/tttcmds/bin ~/Documents/misc/bin $PATH

## tttcmds

    sudo pkg install kyua

    mkdir -p ~/Documents
    cd ~/Documents/
    git clone git@github.com:daichigoto/tttcmds.git
    cd tttcmds
    make

## misc

    mkdir -p ~/Documents
    cd ~/Documents/
    git clone git@github.com:daichigoto/misc.git
    cd misc
    make

## ユーティリティ

    sudo pkg install -y zip
    sudo pkg install -y gsed
    sudo pkg install -y gawk
    sudo pkg install -y GraphicsMagick
    sudo pkg install -y nginx
    sudo pkg install -y vim
    sudo pkg install -y fzf

###### /usr/local/etc/nginx/nginx.conf

    --- /usr/local/etc/nginx/nginx.conf-dist	2021-07-10 02:59:16.000000000 +0900
    +++ /usr/local/etc/nginx/nginx.conf	2021-07-28 19:13:10.824682000 +0900
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
    +	server_name  10.211.55.6;
     
             #charset koi8-r;
     
             #access_log  logs/host.access.log  main;
     
             location / {
    -            root   /usr/local/www/nginx;
    -            index  index.html index.htm;
    +            #root   /usr/local/www/nginx;
    +            #index  index.html index.htm;
    +            root   /Users/daichi/Documents;
    +	    autoindex on;
             }
     
             #error_page  404              /404.html;

###### /usr/local/etc/nginx/mime.types

    --- /usr/local/etc/nginx/mime.types-dist	2021-07-10 02:59:16.000000000 +0900
    +++ /usr/local/etc/nginx/mime.types	2021-07-28 19:13:34.594663000 +0900
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

###### vim

    mkdir -p ~/.cache/vim/dein
    cd ~/.cache/vim/dein/
    curl https://raw.githubusercontent.com/Shougo/dein.vim/master/bin/installer.sh > installer.sh
    sh ./installer.sh .
    rm ./installer.sh

    mkdir -p ~/Documents
    cd ~/Documents/
    git clone git@github.com:daichigoto/config.git
    ./config/tools/install-vim.sh

    vim  ← 処理が完了するまで待機
