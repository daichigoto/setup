# FreeBSDゲスト セットアップ

###### /etc/crontab に追加する設定

    */13    *   *   *   *   root    service ntpdate onestart

###### cron(8) を再起動

    service cron restart

※ 仮想環境が停止から再開すると時刻がずれるため、ntpdate(8)で強制的に時刻を補正する。
