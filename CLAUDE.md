# ヨミクエリ 売上ダッシュボード

## ファイル構成

```
index.html          メインファイル（これだけで全機能）
SPEC.md             仕様書（データ構造・フィールド定義・ページ仕様）
TROUBLESHOOTING.md  トラブルシューティングガイド（0になる・表示されない等）
```

## デプロイ

- 本番URL: https://harac-web.github.io/sales-dashboard/
- masterブランチにpushすれば自動でGitHub Pagesに反映（1〜2分）
- コミットメッセージは `"Update dashboard"` で統一

## 作業ワークフロー

このリポジトリはClaudeのワークツリー機能で管理されている。  
`index.html` を編集したら必ずmasterにpushすること（ローカル変更だけでは本番に反映されない）。

```bash
git add index.html
git commit -m "Update dashboard"
git push origin HEAD:master
```

## GAS API

```
URL: https://script.google.com/macros/s/AKfycbz2mFlkr-i6Y27rAjkmw1ABPY6Xmoun9MPPtmHT4KYUFUSILkH-ZyUZ4SK0SyyzCoPxQw/exec
KEY: yomi-shukei-test
```

レスポンス: `{ success, data, costData, corpoCostData, seikyuuData, companies, updated, count }`

## 重要な規約

- **月ソート値は YYYYMM の6桁整数**（例: 202507）。`mTo` の上限は `999999`
- **金額単位が2種類ある**: 社員人件費シートは万円単位、通常コストは円単位（GASが `sheetSource='employee'` を付与して区別）
- **カテゴリ名は文字列完全一致**: 全角/半角括弧・濁点1文字のズレで0になる

## 困ったときは

まず `TROUBLESHOOTING.md` を確認する。特に「データが全部0」はパターン化済み。
