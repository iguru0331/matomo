# これは？

MatomoをインストールするためのAnsibleプレイブック、Vagrantfileです。
ベースがCentOS7で、以下ソフトウェアがインストールされます。

- apache
- php74(curl, gd, cli, mysql, xml, mbstring)
- mysql57(client, server, common, libs, libs-compat, python)
- matomo 3.14.1

また、おまけでアクセスログ生成用にapache-loggenもインストールされるようになっております。
※不要な場合はroles内のrubyを削除してください。

## 実行環境

```
vagrant: 2.2.10
vagrant box: centos/7 (virtualbox, 2004.01)
vagrant plugin: vagrant-reload (0.0.1, global)
ansible: 2.9.11
```

## 注意点

デフォルトでprivate networkにて192.168.22.11/24に仮想サーバが構築されます。
変更したい場合、Vagrantfileを修正するようお願いします。
