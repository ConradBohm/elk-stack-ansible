required_plugins = ["vagrant-hostsupdater"]
required_plugins.each do |plugin|
    exec "vagrant plugin install #{plugin}" unless Vagrant.has_plugin? plugin
end

Vagrant.configure("2") do |config|

  config.vm.define "elasticsearch" do |els|
      els.vm.box = "ubuntu/xenial64"
      els.vm.network "private_network", ip: "192.168.10.10"
      els.hostsupdater.aliases = ["development.local"]
      config.vm.provision "ansible_local" do |ansible|
        ansible.playbook = "environment/elasticsearch/playbook.yml"
      end
    #  app.vm.provision "shell", inline: set_env({DB_HOST: "mongodb://192.168.10.150:27017/posts"}), privileged: false
    end


end
