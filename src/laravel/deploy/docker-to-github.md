# 【Docker 編】実装したコードを GitHub へ push

いつもどおり GitHub にコードを push する．

## リポジトリの作成

適当につくっておく．

## ソースコードの push

> ローカルでの操作．「コンテナにログインしていない状態」で実行すること．

以下のコマンドを実行する．

必ずプロジェクトのフォルダに`cd`してから実行すること！！

```bash
$ git init
$ git remote add origin YOUR_REPOSITORY_URL
$ git add .
$ git commit -m"first commit"
$ git push origin main
```

GitHub にプロダクトのソースコードが push されていれば OK！
