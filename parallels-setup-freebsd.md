# Parallels Desktop - FreeBSDゲストセットアップ

1. FreeBSDインストーラISOイメージ(aarch64版)を[ダウンロード](https://download.freebsd.org/ftp/releases/arm64/aarch64/ISO-IMAGES/)
2. Parallels Desktop：「ファイル」→「新規」→「続行」→「DVD/イメージファイルからWindows/その他OSをインストール」→「手動で選択する」→ダウンロードしたISOファイルを選択→「続行」→「その他」→「OK」→名前「FreeBSD Virt」→「インストール前に構成をカスタマイズする」にチェック→「作成」
3. Parallels Desktop：「FreeBSD Virtの構成」→「ハードウェア」→プロセッサ「1」※1
4. Parallels Desktop：「FreeBSD Virt」→「▷」

|項目|内容|
|:---|:---|
|Keymap|United States of America|
|Hostname|virt.ongs.co.jp|
|Distribution|kernel-dbg, ports, src|
|Partitioning|Auto (UFS)|
|Timezone|JST (Asia/Japan)|

5. Parallels Desktop：「FreeBSD Virtの構成」→「CD/DVD」→ソース「切断済み」

※1 FreeBSD 13.0-RELEASEはプロセッサが1つでないと動作しない。
