Vagrant.configure(2) do |config|
  config.vm.define "es21" do |node|
        node.vm.box = "bento/centos-6.7"
        node.vm.hostname = "es21"
        node.vm.network :private_network, ip: "192.168.1.41"
        config.vm.provider :virtualbox do |vb|
        #     vb.gui = true
            vb.memory = 1536
        end
  end
end

