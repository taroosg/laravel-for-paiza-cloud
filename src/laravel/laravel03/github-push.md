# GitHub へ push

Paiza Cloud 上で開発したプロダクトをデプロイする場合，下記の手順で行うとスムーズである．

1. Paiza Cloud から GitHub へソースコードを push する．
2. ローカル PC のターミナルでデプロイ先サーバにアクセスし，GitHub のソースコードを clone する．
3. DB など必要に応じてクライアントツールを使用して設定する．

本項では上記「1」の手順を解説する．

## Paiza Cloud 環境の SSH 鍵ファイルの準備

> 💻 Paiza Cloud ターミナルの操作

ホームディレクトリ直下に鍵ファイルを保存するための `.ssh` フォルダを作成し，移動する．

```bash
$ cd ~
$ mkdir .ssh
$ cd .ssh
```

SSH 鍵ファイルを作成する．ファイル名は既定のまま，パスワードは空欄で OK なのでそのまま Enter で進める．

```bash
$ ssh-keygen

Generating public/private rsa key pair.
Enter file in which to save the key (/home/ubuntu/.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/ubuntu/.ssh/id_rsa.
Your public key has been saved in /home/ubuntu/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:33yZ6Zkm1ZNfm28N2zTsii8ZPUX0YnJ27/3DC7a9lDg ubuntu@laravel-test
The key's randomart image is:
+---[RSA 2048]----+
|              .. |
|               ..|
|            . * o|
|             = +.|
|        S   . o.o|
|         . + o+X*|
|          . =EOB@|
|           o+oOO*|
|           .o*==B|
+----[SHA256]-----+

```

公開鍵ファイルの中身を表示する．

```bash
$ cat id_rsa.pub

ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDbFShwJXqs23OuKYHG9EPbHObzWqO1Lua6m/BC4aVyqo82i9tS6ZDKXTXEUMqhtba1WadmXMPEY4yT6f9KSueEHn7lQFWoXSmqGQ1amUSGSPth589k3pnO+83AWwdhb0M4AUv684FX+SCGNBV0o01R63tSmXMf++MzxpvC17rKDPpIjM/olyt3XF+p/IfAJvJUEq7uTHTgqSAXgAc/Epnv8QoT74XiqeA5fLNbcrrFCMKj8kuv5XhAht3K1ryWULduZ0rOUjRosntUxDFyBbM2HWsi+ABKJagxnqkmMAa0dSC5KuZXurtzYOdf1GaR3A/AMr5gX8G2j3/23auUO413 ubuntu@laravel-test
```

## GitHub に公開鍵を設定

> 🌏 ブラウザの操作

GitHub のサイトにアクセスし，「設定」→「SSH keys」へ進む．「Add SSH key」をクリックして入力画面へ進む．

ターミナルに表示された文字列を「ssh-rsa」から全てコピーし，GitHub サイトの入力欄に貼り付ける．タイトルは PC 名など適当につけて OK．
入力したら「Add key」をクリックして終了．

※公開鍵は PC 毎にペアを作成するため，どの PC で発行した公開鍵なのか判別できるように名前をつけると良い．

## Git の設定

> 💻 Paiza Cloud ターミナルの操作

プロジェクトのディレクトリに移動する．

```bash
$ cd ~
$ cd laratter

```

GitHub アカウントの情報を設定する．**必ず自分のアカウントの情報を入力すること．**

```bash
$ git config --global user.name "YOUR_GITHUB_ACCOUNT_NAME"
$ git config --global user.email "YOUR_GITHUB_EMAIL"

```

デフォルトブランチを `main` に変更する．

```bash
$ git config --global init.defaultBranch main
```

## コミットしてプッシュする．

> 🌏 ブラウザの操作

GitHub 上に新規リポジトリを作成しておく．

作成したら，SSH の URL を控えておく．

> 💻 Paiza Cloud ターミナルの操作

```bash
$ git init

# 実行結果
Initialized empty Git repository in /home/ubuntu/laratter/.git/


# ファイルを add -> commit する
$ git add .
$ git commit -m "init"

# 実行結果（中略）
[main (root-commit) 5b761c0] init
 85 files changed, 10026 insertions(+)
 create mode 100644 .editorconfig
 create mode 100644 .env.example
 create mode 100644 tests/Unit/ExampleTest.php
 create mode 100644 webpack.mix.js

# リポジトリの URL （SSH）を設定してpushする．
$ git remote add origin YOUR_REPOSITORY_URL
$ git push origin main

# 実行結果（途中で ` (yes/no)?` と訊かれるので `yes` と入力してEnter）
The authenticity of host 'github.com (52.192.72.89)' can't be established.
RSA key fingerprint is SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'github.com,52.192.72.89' (RSA) to the list of knownhosts.
Counting objects: 110, done.
Delta compression using up to 3 threads.
Compressing objects: 100% (91/91), done.
Writing objects: 100% (110/110), 69.46 KiB | 3.66 MiB/s, done.
Total 110 (delta 7), reused 0 (delta 0)
remote: Resolving deltas: 100% (7/7), done.
To github.com:taroosg/paiza-cloud-test.git
 * [new branch]      main -> main

```

これでソースコードが GitHub に push されれば OK！
