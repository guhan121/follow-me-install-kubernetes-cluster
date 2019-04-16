# 172.27.128.150 m7-autocv-gpu01	m7-autocv-gpu01
# 172.27.128.149 m7-autocv-gpu02	m7-autocv-gpu02
# 172.27.128.148 m7-autocv-gpu03	m7-autocv-gpu03
H = Hash["1" => "172.27.128.150", "2" => "172.27.128.149","3" => "172.27.128.148"]
Vagrant.configure("2") do |config|

  H.each do |i,ip|

    config.vm.define "m7-autocv-gpu0#{i}" do |node|

      # 设置虚拟机的Box
      node.vm.box = "qiantao/ubuntu-xenial"

      # 设置虚拟机的主机名
      node.vm.hostname="m7-autocv-gpu0#{i}"

      # 设置虚拟机的IP
      node.vm.network "private_network", ip: "#{ip}"

      # 设置主机与虚拟机的共享目录 前面是主机目录，后面是测试机木枯
      node.vm.synced_folder "/home/it/vagrant/share", "/home/vagrant/share"

      # VirtaulBox相关配置
      node.vm.provider "virtualbox" do |v|

        # 设置虚拟机的名称
        v.name = "m7-autocv-gpu0#{i}"

        # 设置虚拟机的内存大小
        v.memory = 2048

        # 设置虚拟机的CPU个数
        v.cpus = 1
      end

      # # 使用shell脚本进行软件安装和配置
      # node.vm.provision "shell", inline: <<-SHELL
      #
      # # 安装docker 1.11.0
      # wget -qO- https://get.docker.com/ | sed 's/docker-engine/docker-engine=1.11.0-0~trusty/' | sh
      # usermod -aG docker vagrant
      #
      # SHELL

    end
  end
end