# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = '2'

@scriptM1 = <<SCRIPT
  echo ""
  echo ""
  echo "               ___               "
  echo "              (o,o)              "
  echo "             <  .  >             "
  echo "              -----              "
  echo "+-------------------------------+"
  echo "|          IT-AKADEMY           |"
  echo "| VM LAB AD10 - web1  |"
  echo "+-------------------------------+"
  echo "\n"
  echo "Mise à jour des paquets...\n"
  sudo apt update &> /dev/null
  sudo apt upgrade -y &> /dev/null

  echo "Installation de Git...\n"
  sudo apt install -y git-core &> /dev/null

  echo "Installation d'Apache 2...\n"
  sudo apt install -y apache2 &> /dev/null
  echo "Activation des modules Apache...\n"
  sudo a2enmod rewrite headers expires &> /dev/null
  echo "Redémarrage d'Apache...\n"
  sudo systemctl restart apache2 &> /dev/null

  echo "Configuration de SSH\n"
  sudo sed -e '/PasswordAuthentication no/ s/^#*/#/' -i /etc/ssh/sshd_config
  sudo systemctl restart sshd

  echo "Installation terminée. Connectez-vous avec la commande vagrant ssh\n"
  echo "L'adresse IP locale de votre VM est 192.168.33.101\n"
  echo "Le répertoire local est mappé dans /var/www/html\n"
  echo "Connexion à la console : vagrant ssh web\n"
SCRIPT

@scriptM2 = <<SCRIPT
  echo ""
  echo ""
  echo "               ___               "
  echo "              (o,o)              "
  echo "             <  .  >             "
  echo "              -----              "
  echo "+-------------------------------+"
  echo "|          IT-AKADEMY           |"
  echo "| VM LAB AD10 - web2 |"
  echo "+-------------------------------+"
  echo "\n"
  echo "Mise à jour des paquets...\n"
  sudo apt update &> /dev/null
  sudo apt upgrade -y &> /dev/null

  echo "Installation de Git...\n"
  sudo apt install -y git-core &> /dev/null

  echo "Installation d'Apache 2...\n"
  sudo apt install -y apache2 &> /dev/null
  echo "Activation des modules Apache...\n"
  sudo a2enmod rewrite headers expires &> /dev/null
  echo "Redémarrage d'Apache...\n"
  sudo systemctl restart apache2 &> /dev/null

  echo "Configuration de SSH\n"
  sudo sed -e '/PasswordAuthentication no/ s/^#*/#/' -i /etc/ssh/sshd_config
  sudo systemctl restart sshd

  echo "Installation terminée. Connectez-vous avec la commande vagrant ssh\n"
  echo "L'adresse IP locale de votre VM est 192.168.33.102\n"
  echo "Le répertoire local est mappé dans /var/www/html\n"
  echo "Connexion à la console : vagrant ssh web\n"
SCRIPT

@scriptM3 = <<SCRIPT
  echo ""
  echo ""
  echo "               ___               "
  echo "              (o,o)              "
  echo "             <  .  >             "
  echo "              -----              "
  echo "+-------------------------------+"
  echo "|          IT-AKADEMY           |"
  echo "| VM LAB AD10 - DB1|"
  echo "+-------------------------------+"
  echo "\n"
  echo "Mise à jour des paquets...\n"
  sudo apt update &> /dev/null
  sudo apt upgrade -y &> /dev/null

  echo "Installation de Git...\n"
  sudo apt install -y git-core &> /dev/null

  echo "Installation de MariaDb..."
  sudo apt install -y software-properties-common dirmngr &> /dev/null
  export DEBIAN_FRONTEND=noninteractive
  sudo debconf-set-selections <<< 'mariadb-server mysql-server/root_password password 0000'
  sudo debconf-set-selections <<< 'mariadb-server mysql-server/root_password_again password 0000'
  sudo -E apt install -y mariadb-server &> /dev/null
  sudo mysql -uroot -p0000 -e  "CREATE DATABASE ad10Master;"
  sudo mysql -uroot -p0000 -e  "CREATE USER 'ad10' IDENTIFIED BY '0000';"
  sudo mysql -uroot -p0000 -e "GRANT USAGE ON *.* TO 'ad10'@localhost IDENTIFIED BY '0000';"
  sudo mysql -uroot -p0000 -e "GRANT ALL privileges ON ad10.* TO 'ad10'@localhost;"
  sudo mysql -uroot -p0000 -e  "FLUSH PRIVILEGES;"
  sudo mysql -uroot -p0000 -e  "CREATE DATABASE ad10Slave;"
  sudo mysql -uroot -p0000 -e  "CREATE USER 'ad10' IDENTIFIED BY '0000';"
  sudo mysql -uroot -p0000 -e "GRANT USAGE ON *.* TO 'ad10'@localhost IDENTIFIED BY '0000';"
  sudo mysql -uroot -p0000 -e "GRANT ALL privileges ON ad10.* TO 'ad10'@localhost;"
  sudo mysql -uroot -p0000 -e  "FLUSH PRIVILEGES;"
  echo "Le mot de passe root de MariaDb est : 0000"
  echo "La base de données 'ad10Master' a été créée"
  echo "La base de données 'ad10Slave' a été créée"
  echo "L'utilisateur MariaDB 'ad10' a été créé"
  echo "Le mot de passe de l'utilisateur MariaDb 'ad10' est : 0000 \n"

  echo "Configuration de SSH\n"
  sudo sed -e '/PasswordAuthentication no/ s/^#*/#/' -i /etc/ssh/sshd_config
  sudo systemctl restart sshd

  echo "Installation terminée. Connectez-vous avec la commande vagrant ssh\n"
  echo "L'adresse IP locale de votre VM est 192.168.33.103\n"
  echo "Le répertoire local est mappé dans /var/www/html\n"
  echo "Connexion à la console : vagrant ssh db1\n"
SCRIPT

@scriptM4 = <<SCRIPT
  echo ""
  echo ""
  echo "               ___               "
  echo "              (o,o)              "
  echo "             <  .  >             "
  echo "              -----              "
  echo "+-------------------------------+"
  echo "|          IT-AKADEMY           |"
  echo "| VM LAB AD10 - DB2|"
  echo "+-------------------------------+"
  echo "\n"
  echo "Mise à jour des paquets...\n"
  sudo apt update &> /dev/null
  sudo apt upgrade -y &> /dev/null

  echo "Installation de Git...\n"
  sudo apt install -y git-core &> /dev/null

  echo "Installation de MariaDb..."
  sudo apt install -y software-properties-common dirmngr &> /dev/null
  export DEBIAN_FRONTEND=noninteractive
  sudo debconf-set-selections <<< 'mariadb-server mysql-server/root_password password 0000'
  sudo debconf-set-selections <<< 'mariadb-server mysql-server/root_password_again password 0000'
  sudo -E apt install -y mariadb-server &> /dev/null
  sudo mysql -uroot -p0000 -e  "CREATE DATABASE ad10;"
  sudo mysql -uroot -p0000 -e  "CREATE USER 'ad10' IDENTIFIED BY '0000';"
  sudo mysql -uroot -p0000 -e "GRANT USAGE ON *.* TO 'ad10'@localhost IDENTIFIED BY '0000';"
  sudo mysql -uroot -p0000 -e "GRANT ALL privileges ON ad10.* TO 'ad10'@localhost;"
  sudo mysql -uroot -p0000 -e  "FLUSH PRIVILEGES;"
  echo "Le mot de passe root de MariaDb est : 0000"
  echo "La base de données 'ad10' a été créée"
  echo "L'utilisateur MariaDB 'ad10' a été créé"
  echo "Le mot de passe de l'utilisateur MariaDb 'ad10' est : 0000 \n"

  echo "Configuration de SSH\n"
  sudo sed -e '/PasswordAuthentication no/ s/^#*/#/' -i /etc/ssh/sshd_config
  sudo systemctl restart sshd

  echo "Installation terminée. Connectez-vous avec la commande vagrant ssh\n"
  echo "L'adresse IP locale de votre VM est 192.168.33.104\n"
  echo "Le répertoire local est mappé dans /var/www/html\n"
  echo "Connexion à la console : vagrant ssh db2\n"
SCRIPT

@scriptBastion = <<SCRIPT

  echo ""
  echo ""
  echo "               ___               "
  echo "              (o,o)              "
  echo "             <  .  >             "
  echo "              -----              "
  echo "+-------------------------------+"
  echo "|          IT-AKADEMY           |"
  echo "| VM LAB AD10 - Bastion         |"
  echo "+-------------------------------+"
  echo "\n"
  echo "Mise à jour des paquets...\n"

  sudo apt update &> /dev/null
  sudo apt upgrade -y &> /dev/null

  echo "Installation de Git...\n"
  sudo apt install -y git-core &> /dev/null

  echo "Installation d'Apache 2...\n"
  sudo apt install -y apache2 &> /dev/null
  echo "Activation des modules Apache...\n"
  sudo a2enmod rewrite headers expires &> /dev/null
  echo "Redémarrage d'Apache...\n"
  sudo systemctl restart apache2 &> /dev/null

  echo "Installation du firewall"
  sudo apt install nftables -y
  echo "Configuration du firewall"

  echo "Redémarage du firewall après configuration"
  sudo systemctl restart nftables.service

  echo "Intallation du loadbalancer"
  sudo apt install haproxy -y

  echo "Configuration de SSH\n"
  sudo sed -e '/PasswordAuthentication no/ s/^#*/#/' -i /etc/ssh/sshd_config
  sudo systemctl restart sshd

  echo "Installation terminée. Connectez-vous avec la commande vagrant ssh\n"
  echo "L'adresse IP locale de votre VM est 192.168.33.100\n"
  echo "Le répertoire local est mappé dans /var/www/html\n"
  echo "Connexion à la console : vagrant ssh web\n"
SCRIPT


Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  
  config.vm.define "web1" do |web1|
    web1.vm.box = 'debian/contrib-buster64'
  	web1.vm.box_check_update = true
    web1.vm.network "private_network", ip: "192.168.33.101"
  	# web1.vm.synced_folder "../data", "/vagrant_data", disabled: true
    # web1.vm.synced_folder ".", "/var/www/html", owner: "vagrant", group: "www-data"
    web1.vm.provision 'shell', inline: @scriptM1

    web1.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--memory", "1024"]
      vb.customize ["modifyvm", :id, "--name", "LAB AD10 - S2 - WEB1"]
  		vb.gui = false
    end
  end

  config.vm.define "web2" do |web2|
    web2.vm.box = 'debian/contrib-buster64'
  	web2.vm.box_check_update = true
    web2.vm.network "private_network", ip: "192.168.33.102"
  	# web2.vm.synced_folder "../data", "/vagrant_data", disabled: true
    # web2.vm.synced_folder ".", "/var/www/html", owner: "vagrant", group: "www-data"
    web2.vm.provision 'shell', inline: @scriptM2

    web2.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--memory", "1024"]
      vb.customize ["modifyvm", :id, "--name", "LAB AD10 - S2 - WEB2"]
  		vb.gui = false
    end
  end

  

  config.vm.define "db1" do |db1|
    db1.vm.box = 'debian/contrib-buster64'
  	db1.vm.box_check_update = true
    db1.vm.network "private_network", ip: "192.168.33.103"
  	# db1.vm.synced_folder "../data", "/vagrant_data", disabled: true
    # db1.vm.synced_folder ".", "/var/www/html", owner: "vagrant", group: "www-data"
    db1.vm.provision 'shell', inline: @scriptM3

    db1.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--memory", "512"]
      vb.customize ["modifyvm", :id, "--name", "LAB AD10 - S2 - DB1"]
  		vb.gui = false
    end
  end

  config.vm.define "bastion" do |bastion|
    bastion.vm.box = "debian/contrib-buster64"
    bastion.vm.network "private_network", ip: "192.168.33.100"
    config.vm.network "public_network", bridge: "en0: Wi-Fi (AirPort)"
    bastion.vm.provision 'shell', inline: @scriptBastion

    bastion.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--memory", "512"]
      vb.customize ["modifyvm", :id, "--name", "LAB AD10 - S2 - BASTION"]
  		vb.gui = false
    end
  end

  # config.ssh.forward_agent    = true
  # config.ssh.insert_key       = false
  # config.ssh.private_key_path =  ["~/.vagrant.d/insecure_private_key","~/.ssh/id_rsa"]
  # config.vm.provision :shell, privileged: false do |s|
  #   ssh_pub_key = File.readlines("#{Dir.home}/.ssh/id_rsa.pub").first.strip
  #   s.inline = <<-SHELL
  #     touch /home/$USER/.ssh/authorized_keys
  #     echo #{ssh_pub_key} >> /home/$USER/.ssh/authorized_keys
  #   SHELL
  # end

end