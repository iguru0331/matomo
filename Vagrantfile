# -*- mode: ruby -*-
# vi: set ft=ruby :

# コンフィグ関数
def ConfigCentosEasy(config , hostname , ip)
  config.vm.define hostname do |node|
    # ホスト名、IPアドレス(ブリッジ接続)
    node.vm.hostname = hostname
    node.vm.network "private_network", ip: ip
#    node.vm.network "public_network", ip: ip
    # 起動時実行コマンド
      # - タイムゾーンを日本に設定
      # - パスワード認証有効化(鍵不要)
      # - sshd_config変更に伴うsshd再起動
    node.vm.provision "shell", inline: <<-SHELL
      timedatectl set-timezone Asia/Tokyo
#      sed -i "s/PasswordAuthentication no/PasswordAuthentication yes/" /etc/ssh/sshd_config
#      systemctl restart sshd
      SHELL
  end

  config.vm.provider "virtualbox" do |vb|
    # メモリ512MB
    vb.memory = "512"
    # CPU数1台
    vb.cpus = "1"
  end
end

# 本処理
Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  # vagrants
  ConfigCentosEasy(config, "vagrant" , "192.168.22.11")

  # Ansibleによるプロビジョニング
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/site.yml"
    ansible.limit = 'all'
  end

  # 再起動
  config.vm.provision "reload"

end
