# このリポジトリについて

MatomoをインストールするためのAnsibleプレイブック、Vagrantfileです。

ベースがCentOS7で、以下ソフトウェアがインストールされます。

- apache
- php74(curl, gd, cli, mysql, xml, mbstring)
- mysql57(client, server, common, libs, libs-compat, python)
- matomo 3.14.1

また、おまけでアクセスログ生成用にapache-loggenもインストールされるようになっております。

※不要な場合はroles内のrubyを削除してください。

# 実行環境

```
vagrant: 2.2.10
vagrant box: centos/7 (virtualbox, 2004.01)
vagrant plugin: vagrant-reload (0.0.1, global)
ansible: 2.9.11
```

# 使用方法

適当なディレクトリに当リポジトリをクローンし、```vagrant up```を実行してください。

実行後、```http://IPアドレス/matomo```をブラウザで開くとMatomoの設定画面が表示れますので、適宜進めてください。

なお、DB設定は以下の通りです。

| 項目 | 値 |
|:--|:--|
|データベース・サーバー|127.0.0.1|
|ログイン|matomo|
|パスワード|Vagrant@1|
||データベース名|matomo|

また、```http://IPアドレス/test.html```にテストページを作成しておりますので、トラッキングコードを設定して挙動確認するなどでご利用ください。

# 注意点

デフォルトでprivate networkにて192.168.22.11/24に仮想サーバが構築されます。

変更したい場合、Vagrantfileを修正するようお願いします。
