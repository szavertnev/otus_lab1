# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # Указываем образ Ubuntu 
  config.vm.box = "ubuntu/focal64" 
  
  # Настройки виртуальной машины
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"  # 2 ГБ RAM
    vb.cpus = 2         # 2 CPU
    vb.name = "otus_test"
  end

  # Проброс портов
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # Автоматическая установка ПО
  config.vm.provision "shell", inline: <<-SHELL
    # Обновление системы
    sudo apt-get update -y
    sudo apt-get upgrade -y

    # Установка базовых утилит
    sudo apt-get install -y vim traceroute net-tools tcpdump curl wget git

    # Установка Ansible
    sudo apt-get install -y ansible

    # Проверка версий
    echo "=== Версии установленного ПО ==="
    vagrant --version
    ansible --version
  SHELL

  # (Опционально) Автоматический запуск Ansible-playbook после развертывания
  # config.vm.provision "ansible" do |ansible|
  #   ansible.playbook = "playbook.yml"
  # end
end
