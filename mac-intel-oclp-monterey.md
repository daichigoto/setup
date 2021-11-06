# macOS Monterey インストール方法 (OpenCore Legacy Patcherを使う方法)

## USBメモリをフォーマット

1. 16GB～32GBサイズのUSBメモリをMacへ接続
2. ディスクユーティリティ：「表示」→「すべてのデバイスを表示」→USBボリュームではなくUSBメモリそのものを選択
3. ディスクユーティリティ：「消去」→下記項目を入力および選択→「消去」

|項目|内容|
|:---|:---|
|名前|MyVolume|
|フォーマット|Mac OS拡張 (ジャーナリング)|
|スキーマ|GUIDパーティションマップ|

## macOS Monterey インストールメディアを作成

フォーマットしたUSBメモリを接続してから次の作業を行う。

    [ ! -d ~/macOS-installer/ ] && mkdir ~/macOS-installer; cd ~/macOS-installer; [ ! -f ~/macOS-installer/installinstallmacos.py ] && curl -O https://raw.githubusercontent.com/munki/macadmin-scripts/main/installinstallmacos.py ; sudo python installinstallmacos.py	← 途中でMontereyの番号を入力
    open Install_macOS_*.dmg
    open /Applications
    「macOS Montereyインストール」を「/Applications」へコピー
    sudo /Applications/Install\ macOS\ Monterey.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume	← 途中でYを入力

[Releases · dortania/OpenCore\-Legacy\-Patcher](https://github.com/dortania/Opencore-Legacy-Patcher/releases)から「OpenCore Legacy Patcher」のTUI版をダウンロードし、展開して実行する。

1. 「Build OpenCore」を選択(1を入力)→「Enter」
2. 「Install OpenCore to USB/internal drive」を選択(2を入力)→USBメモリを選択→EFIパーティションを選択(210MBほどのEFIのパーティション)→「Enter」→「Q」で終了

## macOS Monterey インストール

1. 「Option」を押し続けてMacブートピッカーを起動
2. 「EFI Boot」を選択→OpenCore Legacy Patcherのブートピッカーが表示されたら2秒以内に「Install macOS Monterey」を選択
3. (クリーンインストールする場合) 復旧：「ディスクユーティリティ」→「続ける」→「Macintosh HD」を選択→「消去」→下記項目を入力および選択→「消去」→「完了」→「ディスクユーティリティ」→「ディスクユーティリティを終了」

|項目|内容|
|:---|:---|
|選択対象|Macintosh HD|
|名前|Macintosh HD|
|フォーマット|APFS|

4. 復旧：「macOS Montereyインストール」→「続ける」→「続ける」…　「Macintosh HD」へmacOS Montereyをインストールする作業を進める (何度か再起動がかかる)

## USBインストールメディアなしで起動できるように設定

[Releases · dortania/OpenCore\-Legacy\-Patcher](https://github.com/dortania/Opencore-Legacy-Patcher/releases)から「OpenCore Legacy Patcher」のTUI版をダウンロードし、展開して実行する。

1. 「Build OpenCore」を選択(1を入力)→「Enter」
2. 「Install OpenCore to USB/internal drive」を選択(2を入力)→macOS Montereyをインストールしたディスクを選択→EFIパーティションを選択(210MBほどのEFIのパーティション)→「Enter」→「Q」で終了
3. USBメモリを抜いた状態でシステムを再起動し、macOS Montereyが起動することを確認

## 参考

- [OpenCore Legacy Patcher](https://dortania.github.io/OpenCore-Legacy-Patcher/) 
- []()
