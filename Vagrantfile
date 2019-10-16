$script = <<-SCRIPT
sudo apt-get update
wget --no-check-certificate -O Dynatrace-OneAgent-Linux-latest.sh "https://syb31902.sprint.dynatracelabs.com/api/v1/deployment/installer/agent/unix/default/latest?Api-Token=INSERT_API_TOKEN_HERE&arch=x86&flavor=default"
sudo /bin/sh Dynatrace-OneAgent-Linux-latest.sh APP_LOG_CONTENT_ACCESS=1 INFRA_ONLY=0
wget --no-check-certificate -O Dynatrace-ActiveGate-latest.sh "https://syb31902.sprint.dynatracelabs.com/api/v1/deployment/installer/gateway/unix/latest?Api-Token=INSERT_API_TOKEN_HERE&arch=x86&flavor=default"  
sudo /bin/sh Dynatrace-ActiveGate-latest.sh
SCRIPT



Vagrant.configure("2") do |config|
  config.vm.provider "virtualbox" do |v|
    v.memory = 2048
    v.cpus = 2
  end

  config.vm.box = "ubuntu/bionic64"
  config.vm.provision "shell", inline: $script
  config.vm.hostname = "ActiveGate-SaaS"
  config.vm.network "private_network", ip: "192.168.7.11"
end


