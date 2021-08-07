# 新規購入M1 Mac時 セットアップ

## 基本

- 「このMacについて」→「ソフトウェア・アップデート…」
- システム環境設定：「共有」→「コンピュータ名」
- システム環境設定：「Apple ID」→「Apple ID」
- 移行アシスタント
- 周辺機器セットアップ
- システム環境設定：「一般」→「外観モード」→「ダークモード」
- App Store: 「Display Menu」→「入手」
- [AppCleaner](https://freemacsoft.net/appcleaner/)インストール
- [f.lux](https://justgetflux.com/)インストール
- 不要アプリケーションの調査およびアンインストール
- Dock整理

## ショートカットキー

- システム環境設定：「キーボード」→「音声入力」→「ショートカット」→「オフ」

## マウスカーソル

- システム環境設定：「アクセシビリティ」→「ディスプレイ」→「カーソル」→「カーソルサイズ」→大きめに変更

## Homebrew

###### インストール方法

    /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"  
    echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile  
    eval "$(/opt/homebrew/bin/brew shellenv)"

※ [Homebrew](https://brew.sh/)に掲載されている最新のインストール方法を参照すること。

## ユーティリティ

    brew install bat
