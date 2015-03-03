
Vagrant.configure("2") do |config|
  enable_package_cache(config)
  config.vm.synced_folder '.', '/vagrant', disabled: true
  config.ssh.password = 'vagrant'
  #all params are optional
  create_vm(config) #node-01
  create_vm(config, id: 2, memory: 1024, cpus: 1, box: "chef/centos-7.0")
  create_vm(config, name: "node", id: 3)
end

def create_vm(config, options = {})
  name = options.fetch(:name, "node")
  id = options.fetch(:id, 1)
  vm_name = "%s-%02d" % [name, id]

  box = options.fetch(:box, "chef/centos-7.0")
  memory = options.fetch(:memory, 1024)
  cpus = options.fetch(:cpus, 1)

  config.vm.define vm_name do |config|
    config.vm.box = box
    config.vm.hostname = vm_name
    vm_ip = "192.168.1.10#{id}"
    config.vm.network :private_network, ip: vm_ip

    config.vm.provider :virtualbox do |vb|
      vb.memory = memory
      vb.cpus = cpus
    end
  end
end

def enable_package_cache(config)
  if Vagrant.has_plugin?("vagrant-cachier")
    config.cache.scope = :box
  end
end
