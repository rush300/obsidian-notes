- LAMP Stack (revisited)
	- Common
	- Web
	- Database
- Configuration
- Working with Multiple VMs
- Test Networking
```bash
cd /vagrant
cd scripts
vi centos-common.sh
>#!/bin/bash
>yum update -y --exclude=kernel
>yum install -y nano git unzip screen nc telnet
>:wq!

vi centos-web.sh
#!/bin/bash
#Apache
>yum install -y httpd httpd-devel httpd-tools
>chkconfig --add httpd
>chkconfig httpd on
>service httpd stop
>
>rm -rf /var/www/html
>ln -s /vagrant /var/www/html
>
>service httpd start
>
># PHP
>yum install -y php php-cli php-common php-devel php-mysql
>
>
># Download starter content
>cd /vagrant
>sudo -u vagrant wget -q >https://github.com/rush300/vagrant/tree/main/files/index.html
>sudo -u vagrant wget -q >https://github.com/rush300/vagrant/tree/main/files/info.php

>service httpd restart
>:wq!

vi centos-database.sh
>#!/bin/bash
># MySQL
>
>yum install -y mysql mysql-server mysql-devel
>chkconfig --add mysqld
>chkconfig mysql start
>
>mysql -u root -e "SHOW DATABASES";
>:wq!

cd /projects
git init multi-vms
cd multi-vms
cp ../shell-lamp/Vagrantfile .
vi Vagrantfile
Vagrant.configure("2") do |config|
  
  config.vm.box = "centos/7"

  config.vbguest.auto_update = false
  config.vm.provision "file",
    source: "C:\\Users\\uroot\\vagrant\\files\\git-config",
    destination: "~/.gitconfig"

  config.vm.provision "shell", path: "https://github.com/rush300/vagrant/blob/main/files/scripts/centos-common.sh"

  config.vm.define "web" do |web|
    web.vm.hostname = "web-server"

    web.vm.network "forwarded_port", guest: 80, host: 8080

    web.vm.network "private_network", ip: "192.168.10.24"

    web.vm.provision "shell", path: "https://github.com/rush300/vagrant/blob/main/files/scripts/centos-web.sh"

  end
  config.vm.define "db" do |db|
    db.vm.hostname = "database-server"

    db.vm.network "private_network", ip: "192.168.10.25"

    db.vm.provision "shell", path: "https://github.com/rush300/vagrant/blob/main/files/scripts/centos-database.sh"
  end
:wq!

vagrant up web
vagrant status
vagrant up db

vagrant ssh web/db
vagrant halt
vagrant destroy
```