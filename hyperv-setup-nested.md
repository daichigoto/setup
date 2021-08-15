# ネスト仮想化 セットアップ

    仮想マシン終了
    Set-VMProcessor -VMName '仮想マシン名' -ExposeVirtualizationExtensions $true
    Get-VMProcessor -VMName '*' ft VMName,ExposeVirtualizationExtensions
    システム再起動

# 参考

- [仮想環境のWindowsでLinuxアプリケーションやコマンドを実行する方法 \| TECH\+](https://news.mynavi.jp/article/20210724-1915386/)
