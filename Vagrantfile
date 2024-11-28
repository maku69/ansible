Vagrant.configure("2") do |config|

  # Ühine võrk ansible_markus
  config.vm.network "private_network", type: "dhcp", virtualbox__intnet: "ansible_markus"

  # Debian 12 - markus-dockerhost
  config.vm.define "markus-dockerhost" do |dockerhost|
    dockerhost.vm.box = "debian/bullseye64"
    dockerhost.vm.hostname = "markus-dockerhost"
    dockerhost.vm.network "private_network", ip: "10.10.10.130", netmask: "255.255.255.128"
    dockerhost.vm.provider "virtualbox" do |vb|
      vb.memory = "8192"
      vb.cpus = 4
    end
    dockerhost.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y fish tmux mc wget tree git
      sudo apt-get install -y docker.io
    SHELL
  end

  # Debian 12 - markus-ansible
  config.vm.define "markus-ansible" do |ansible|
    ansible.vm.box = "debian/bullseye64"
    ansible.vm.hostname = "markus-ansible"
    ansible.vm.network "private_network", ip: "10.10.10.131", netmask: "255.255.255.128"
    ansible.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y fish tmux mc wget tree git
      sudo apt-get install -y ansible sshpass yamllint ansible-lint
    SHELL
  end

  # Ubuntu 24.04 - markus-ubuntu
  config.vm.define "markus-ubuntu" do |ubuntu|
    ubuntu.vm.box = "ubuntu/jammy64"
    ubuntu.vm.hostname = "markus-ubuntu"
    ubuntu.vm.network "private_network", ip: "10.10.10.132", netmask: "255.255.255.128"
    ubuntu.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y fish tmux mc wget tree git
    SHELL
  end

  # CentOS Stream 9 - markus-centos
  config.vm.define "markus-centos" do |centos|
    centos.vm.box = "CrunchyData/stream9"
    centos.vm.hostname = "markus-centos"
    centos.vm.network "private_network", ip: "10.10.10.133", netmask: "255.255.255.128"
    centos.vm.provision "shell", inline: <<-SHELL
      sudo yum update -y
      sudo yum install -y fish tmux mc wget tree git
    SHELL
  end

  # OpenSUSE Leap - markus-opensuse
  config.vm.define "markus-opensuse" do |opensuse|
    opensuse.vm.box = "opensuse/Leap-15.6.x86_64"
    opensuse.vm.hostname = "markus-opensuse"
    opensuse.vm.network "private_network", ip: "10.10.10.134", netmask: "255.255.255.128"
    opensuse.vm.provision "shell", inline: <<-SHELL
      sudo zypper update -y
      sudo zypper install -y fish tmux mc wget tree git
    SHELL
  end

end
