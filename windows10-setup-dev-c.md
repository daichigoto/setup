# C言語開発環境セットアップ

## LLVM Clang + Visual Studio Build Toolsセットアップ

###### インストール方法

    winget install Microsoft.WindowsTerminalPreview
    winget install Microsoft.PowerShell
    winget install Microsoft.VisualStudio.2019.BuildTools
    winget install Python.Python.3
    winget install LLVM.LLVM
    winget install Microsoft.VisualStudioCode
    winget install Git.Git
    winget install GnuWin32.Make

1. 環境変数PATHに「C:\Program Files\LLVM\bin」と「C:\Program Files\Git\bin」を追加。
2. 設定アプリケーション：「アプリ」→「アプリと機能」→「Visual Studio Build Tools 2019」→「変更」→「C++によるデスクトップ環境」にチェックを入れ→「変更」→システムを再起動
3. Visual Studio Code：「Extensions」→「CodeLLDB」→「Install」
4. Visual Studio Code：「Extensions」→「clangd」→「Install」

※ Visual Studio Build Tools 2019 (Microsoft.VisualStudio.2019.BuildTools)をインストールすることで、依存関係で次のソフトウェアがインストールされる。

- Microsoft Visual C++ 2015-2019 Redistributable (x64)
- Microsoft Visual C++ 2-15-2019 Redistributable (x86)
- Microsoft Visual Studio Installer
- Microsoft Windows Dekstop Runtime (x64)
- Windows SDK AddOn
- Windows Software Development Kit - Windows

###### tasks.json

    {
        "version": "2.0.0",
        "tasks": [
            {
                "label": "Clang",
                "type": "process",
                "command": "clang.exe",
                "args": [
                    "-g",
                    "${file}",
                    "-o",
                    "${fileDirname}/${fileBasenameNoExtension}.exe"
                ],
                "problemMatcher": [],
                "group": {
                    "kind": "build",
                    "isDefault": true
                }
            }
        ]
    }

###### launch.json

    {
        "version": "0.2.0",
        "configurations": [
            {
                "type": "lldb",
                "request": "launch",
                "name": "Debug",
                "program": "${workspaceFolder}/${fileBasenameNoExtension}.exe",
                "args": [],
                "cwd": "${workspaceFolder}"
            }
        ]
    }

## LLVM Clang in Cygwinセットアップ

###### インストール方法

    winget install Microsoft.VisualStudioCode
    winget install Microsoft.WindowsTerminalPreview
    winget install Microsoft.PowerShell
    winget install Git.Git

###### [Cygwin](https://www.cygwin.com/)インストール

|操作|内容|
|:---|:---|
|追加するパッケージ|make, clang|

1. 環境変数PATHに「C:\msys64\usr\bin」と「C:\Program Files\Git\bin」を追加。
2. Visual Studio Code：「Extensions」→「CodeLLDB」→「Install」
3. Visual Studio Code：「Extensions」→「clangd」→「Install」

###### tasks.json

###### launch.json

## LLVM Clang in MSYS2セットアップ

###### インストール方法

    winget install Microsoft.VisualStudioCode
    winget install Microsoft.WindowsTerminalPreview
    winget install Microsoft.PowerShell
    winget install Git.Git
    winget install MSYS2

1. 環境変数PATHに「C:\msys64\usr\bin」と「C:\Program Files\Git\bin」を追加。
2. Visual Studio Code：「Extensions」→「CodeLLDB」→「Install」
3. Visual Studio Code：「Extensions」→「clangd」→「Install」

###### 開発ツールインストール方法

    pacman -Syu
    pacman -S make
    pacman -S clang
    pacman -S msys2-runtime-devel

###### tasks.json

###### launch.json

# 参考

- [【連載】Windows 10で始めるC言語開発 \| TECH\+](https://news.mynavi.jp/series/c-for-windows/)
