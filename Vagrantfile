Vagrant.configure('2') do |config|
  config.vm.box = 'centos/7'
  config.vm.network 'public_network'
  config.vm.synced_folder '.', '/vagrant', type: 'rsync'
  config.vm.hostname = 'wordpress'
  config.vm.define 'wordpress'

  config.vm.provider 'virtualbox' do |vb|
    vb.memory = '2048'
    vb.cpus = 2
    vb.name = 'wordpress'
  end

  config.vm.provision 'ansible_local' do |ansible|
    ansible.limit = 'all'
    ansible.compatibility_mode = '2.0'
    ansible.provisioning_path = '/vagrant'
    ansible.playbook = 'provisioning/main.yml'
  end
end