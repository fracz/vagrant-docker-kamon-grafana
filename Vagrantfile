unless Vagrant.has_plugin?("vagrant-docker-compose")
  system("vagrant plugin install vagrant-docker-compose")
  puts "Dependencies installed, please try the command again."
  exit
end

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/trusty64"

  config.vm.network(:forwarded_port, guest: 80, host: 9080)
  config.vm.network(:forwarded_port, guest: 81, host: 9081)
  config.vm.network(:forwarded_port, guest: 8125, host: 8125, protocol: "udp")
  config.vm.network(:forwarded_port, guest: 8126, host: 8126)
  
  config.vm.provision :docker
  config.vm.provision :docker_compose, yml: "/vagrant/docker-compose.yml", rebuild: true, run: "always"
end