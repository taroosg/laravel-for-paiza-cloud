# Laravel 03

## 本日の内容

- マイページの実装（1 対多のデータ）．
- ユーザ名の表示（多対 1 のデータ）．
- favorite 機能の実装（多対多）．

## 本日の目標

- SNS アプリケーションを完成させる．
- 様々な形のデータを扱う方法を学ぶ．
- Laravel でアプリケーションを開発するイメージを持つ．

## ルーティング表

都度確認しよう！

```txt
+--------+-----------+-----------------------+----------------+-----------------------------------------------------+-----------------+
| Domain | Method    | URI                   | Name           | Action                                              | Middleware      |
+--------+-----------+-----------------------+----------------+-----------------------------------------------------+-----------------+
|        | GET|HEAD  | tweet                 | tweet.index    | App\Http\Controllers\TweetController@index          | web             |
|        | POST      | tweet                 | tweet.store    | App\Http\Controllers\TweetController@store          | web             |
|        | GET|HEAD  | tweet/create          | tweet.create   | App\Http\Controllers\TweetController@create         | web             |
|        | GET|HEAD  | tweet/{tweet}         | tweet.show     | App\Http\Controllers\TweetController@show           | web             |
|        | PUT|PATCH | tweet/{tweet}         | tweet.update   | App\Http\Controllers\TweetController@update         | web             |
|        | DELETE    | tweet/{tweet}         | tweet.destroy  | App\Http\Controllers\TweetController@destroy        | web             |
|        | GET|HEAD  | tweet/{tweet}/edit    | tweet.edit     | App\Http\Controllers\TweetController@edit           | web             |
+--------+-----------+-----------------------+----------------+-----------------------------------------------------+-----------------+
```

## 多用するコマンドなどまとめ

※ここでは実行しません！！ 開発中に忘れたら見よう！

### Laravel アプリケーションの立ち上げ

```bash
$ php artisan serve
```

### Laravel アプリケーション画面の確認

上記コマンド実行後，左側の「8080」をクリック．

### phpmyadmin 画面の確認

左側の「80」をクリックし，表示された画面の URL の後に `/phpmyadmin` を追加．
