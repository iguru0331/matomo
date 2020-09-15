# matomo
matomoをvagrant,ansibleで構築したもの

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
