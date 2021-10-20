# ロリポップマネージドクラウドと GitHub の SSH 通信設定

ここまででローカル PC からマネージドクラウド上の仮想マシンを操作できるようになった．

続いて，マネージドクラウド上に GitHub のソースコードをデプロイするため，両者の間で通信できるように設定を行う．

## ssh-key の発行

> Lolipop での操作

ssh-key を作成し，マネクラと GitHub の間で通信できるようにする．

```bash
$ cd .ssh
$ ssh-keygen
```

実行結果

```bash
Generating public/private rsa key pair.
Enter file in which to save the key (/var/www//.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /var/www//.ssh/id_rsa.
Your public key has been saved in /var/www//.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:NPkD2j3bgqXWJ2G2nO2hMjGh3pZwruePjPnFosuUuPc reliable-amami-8204@ssh-aws-laravel01.lolipop.io-2adc16106d
The key's randomart image is:
+---[RSA 2048]----+
|                 |
|         .       |
|        =        |
|       +.=       |
|      ..w.w      |
|     .w.+w w     |
|    ..w==+@ =    |
|     +w*w+ * .   |
|    ..www+w .    |
+----[SHA256]-----+
```

## ssh-key の表示と登録

作成した ssh-key を表示する．

```bash
$ cat id_rsa.pub
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDJPmXzhA733dAupv+pVUG6I04agsUSKI7BeekJgBn//1P7Ca96JJkqd1M8yBHARSJxYdSUC31Dn9UpmO87XVLVlVCjmwwwwwwwwwwwwwwwwzIqvRtJmOfvQEfJ/cvBA/bPkrD3V80epwlWiVfWNPSKIZYKVf3LRJI2RoU8WtNSI/Zc8VOH+NOxRVQRQrYaHUSjKDqwFqKK/ttuG4xoRHXPI4Xj4rNn+zfNcd52z0Njq/TtpOAZ6TH6Xtg366sc60HJpIBcQfiz8Kq1mpmw5aLqTzz2l6V0rbsQB0zZCIaqdpFdRUf47aMRBpqK10LPB9N8jC3Gq5Gb1WuJY5Asbzxp reliable-amami-8204@ssh-aws-laravel01.lolipop.io-2adc16106d
```

> ブラウザでの操作

上記で表示された GitHub サイトに ssh-key を登録する．流れはこれまでと同様．
