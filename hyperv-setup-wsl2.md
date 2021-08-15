# ゲストWSL2 セットアップ

仮想マシンでWSL2を使うには、ホストでネスト仮想化を有効化する必要がある。有効化方法は次のとおり。

    仮想マシン終了
    Set-VMProcessor -VMName '仮想マシン名' -ExposeVirtualizationExtensions $true
    Get-VMProcessor -VMName '*' ft VMName,ExposeVirtualizationExtensions
    システム再起動

# 参考

- [仮想環境のWindowsでLinuxアプリケーションやコマンドを実行する方法 \| TECH\+](https://news.mynavi.jp/article/20210724-1915386/)
