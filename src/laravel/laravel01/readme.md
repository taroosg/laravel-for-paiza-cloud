# Laravel 01

## 本日の内容

- MVC フレームワークについての解説．
- 開発環境についての解説．
- SNS アプリケーションの実装（データ作成，一覧表示まで）．

## 本日の目標

- MVC フレームワークである Laravel の動き方や考え方を学ぶ．
- SNS アプリケーションの実装を通して，開発の手順や流れに慣れる．
- PHP での実装と Laravel での実装について，共通点や相違点を把握する．

## ルーティング表

後ほど解説します！

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
