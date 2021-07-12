# C言語開発環境(LLVM) セットアップ

    winget install "Windows Terminal"
    winget install PowerShell
    winget install "Visual Studio Build Tools 2019"
    winget install Python.Python.3
    winget install LLVM
    winget install "Visual Studio Code"
    winget install Git.Git
    winget install GnuWin32.Make

1. 環境変数PATHに「C:\Program Files\LLVM\bin」と「C:\Program Files\Git\bin」を追加。
2. 設定アプリケーション：「アプリ」→「アプリと機能」→「Visual Studio Build Tools 2019」→「変更」→「C++によるデスクトップ環境」にチェックを入れ→「変更」→システムを再起動
3. Visual Studio Code：「Extensions」→「CodeLLDB」→「Install」
3. Visual Studio Code：「Extensions」→「clangd」→「Install」

##### tasks.json

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

##### launch.json

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
