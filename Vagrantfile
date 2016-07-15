VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "centos/7"
  config.vm.network "private_network", type: "dhcp"

  config.vm.provision :ansible do |ansible|
    ansible.playbook = "prometheus.yml"
    ansible.verbose = 'vvvvvvv'
    end
end
