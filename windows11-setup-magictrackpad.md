# Apple Magic Trackpad セットアップ

###### Bluetoothペアリング

1. Apple Magic Trackpadの電源ON
2. 設定アプリケーション：「Bluetoothとデバイス」→「デバイスの追加」
3. デバイスを追加する：「Bluetooth」→「Magic Trackpad」→「完了」

###### ドライバインストール方法

1. [imbushuo/mac\-precision\-touchpad: Windows Precision Touchpad Driver Implementation for Apple MacBook / Magic Trackpad](https://github.com/imbushuo/mac-precision-touchpad)をダウンロード
2. AmtPtpDevice.infをインストール

###### ドライバアンインストール方法

1. システムを再起動
2. デバイスマネージャを起動
3. デバイスマネージャ：「Apple Precision Touch Device」→「デバイスのアンインストール」→「このデバイスのドライバーを削除しようとしました」にチェック→「アンインストール」
4. デバイスマネージャ：「Apple Multi-touch Trackpad HID filter」→「デバイスのアンインストール」→「このデバイスのドライバーを削除しようとしました」にチェック→「アンインストール」
5. デバイスマネージャ：「Apple Multi-touch Auxiliary Services」→「デバイスのアンインストール」→「このデバイスのドライバーを削除しようとしました」にチェック→「アンインストール」
6. デバイスマネージャ：「ハードウェア変更のスキャン」
7. システムを再起動

# 参考

- [WindowsでMacのマジックトラックパッドを使う方法](https://news.mynavi.jp/techplus/article/20220330-2307385/)
