# 「Caps Lock」を「Ctrl」へ入れ替える方法

## Ctrl2Cap

- [Ctrl2Cap](https://docs.microsoft.com/en-us/sysinternals/downloads/ctrl2cap)

##### 「Caps Lock」を「Ctrl」へ入れ替える方法

    .\ctrl2cap.exe /install
    システムの再起動

##### 「Caps Lock」と「Ctrl」の入れ替えを戻る方法

    .\ctrl2cap.exe /uninstall
    システムの再起動

## PowerToys

- [PowerToys](https://docs.microsoft.com/en-us/windows/powertoys/install)

##### インストール方法

    winget install powertoys

1. 「全般」→「常に管理者として実行する」→「オン」
2. 「全般」→「起動時に実行する」→「オン」
3. 「Keyboard Manager」→「キーの再マップ」：「Caps Lock」→「Ctrl (Left)」

## 備考

1. Ctrl2Capは優先度が高い
2. PowerToysは優先度が低い
3. PowerToysの「キーの再マップ」は仮想環境ゲストと相性が悪い
