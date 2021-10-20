# Laravel 02

## 本日の内容

- SNS アプリケーションの実装（詳細表示，更新処理，削除処理）
- ユーザ情報の利用

## 本日の目標

- CRUD 処理の流れをマスターする．
- ユーザ情報の取得や取得したデータの使い方を学ぶ．
- データを連携させる処理を実装する．

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
