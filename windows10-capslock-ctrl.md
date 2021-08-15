# 「Caps Lock」を「Ctrl」へ入れ替えるセットアップ

## Ctrl2Cap

- [Ctrl2Cap](https://docs.microsoft.com/en-us/sysinternals/downloads/ctrl2cap)

###### インストール方法

    ZIPファイルを展開

###### 「Caps Lock」を「Ctrl」へ入れ替え

    .\ctrl2cap.exe /install
    システムの再起動

###### 元に戻す

    .\ctrl2cap.exe /uninstall
    システムの再起動

## PowerToys

- [PowerToys](https://docs.microsoft.com/en-us/windows/powertoys/install)

###### インストール方法

    winget install powertoys

1. 「全般」→「常に管理者として実行する」→「オン」
2. 「全般」→「起動時に実行する」→「オン」
3. 「Keyboard Manager」→「キーの再マップ」：「Caps Lock」→「Ctrl (Left)」

## 備考

1. Ctrl2Capは優先度が高い
2. PowerToysは優先度が低い
3. PowerToysの「キーの再マップ」は仮想環境ゲストと相性が悪い

# 参考

- [Windows 10で「CapsLock」と「Ctrl」を入れ替える方法【PowerToys編】 \| TECH\+](https://news.mynavi.jp/article/20210609-1900755/)
