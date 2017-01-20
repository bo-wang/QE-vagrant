Vagrant.configure(2) do |config|
config.vm.define "windows10", autostart: false do |windows10|
    #windows10.vm.box = "senglin/win-10-enterprise-vs2015community"
	windows10.vm.box ="albumprinter/gv-workstation-win10"
    windows10.vm.box_url = "file:////vistaprint.net/amsterdam/Share/Exchange%20Folder/Gusztav/vagrant/albumprinter--gv-windows10ee-default--0.4.0--virtualbox.box"

    windows10.vm.provider "virtualbox" do |virtualbox|
      virtualbox.name = "windows10.workstation.vagrant"
    end

    # windows10.vm.network "private_network", ip: "172.16.144.15"
	windows10.vm.network :forwarded_port, guest: 3389, host: 13389, id: "rdp", auto_correct: true

    windows10.vm.provision "shell", inline: "cinst git -y"
    windows10.vm.provision "shell", inline: "cinst svn -y"
    windows10.vm.provision "shell", inline: "cinst jdk8 -y"
    windows10.vm.provision "shell", inline: "cinst maven -y"
    windows10.vm.provision "shell", inline: "cinst intellijidea-community -y"
  end
 
config.vm.define "javamachine", autostart: false do |javamachine|
    javamachine.vm.box = "albumprinter/gv-java-workstation-8"
    javamachine.vm.box_url = "file:////vistaprint.net/amsterdam/Share/Exchange%20Folder/Bo%20Wang/Vagrant/QE-Vagrant/albumprinter--gv-java-workstation-8--0.3.0--virtualbox.box"

    javamachine.vm.provider "virtualbox" do |virtualbox|
      virtualbox.name = "javamachine.workstation.vagrant"
    end

    # javamachine.vm.network "private_network", ip: "172.16.144.15"
    javamachine.vm.network :forwarded_port, guest: 3389, host: 23389, id: "rdp", auto_correct: true  
  end

config.vm.define "javaworkshop", autostart: false do |javaworkshop|
    javaworkshop.vm.box = "albumprinter/workstation-win10-javaworkshop"
    javaworkshop.vm.box_url = "file:////vistaprint.net/amsterdam/Share/Exchange%20Folder/Gusztav/vagrant/albumprinter--gv-windows10ee-default--0.4.0--virtualbox.box"

    javaworkshop.vm.provider "virtualbox" do |virtualbox|
      virtualbox.name = "javaworkshop.workstation.vagrant"
    end

    # windows10.vm.network "private_network", ip: "172.16.144.15"
	javaworkshop.vm.network :forwarded_port, guest: 3389, host: 33389, id: "rdp", auto_correct: true

    javaworkshop.vm.provision "shell", inline: "cinst git -y"
    javaworkshop.vm.provision "shell", inline: "cinst svn -y"
    javaworkshop.vm.provision "shell", inline: "cinst jdk8 -y"
    javaworkshop.vm.provision "shell", inline: "cinst maven -y"
    javaworkshop.vm.provision "shell", inline: "cinst intellijidea-community -y"
	javaworkshop.vm.provision "shell", inline: "cinst teamcity -y"
	javaworkshop.vm.provision "shell", inline: "cinst firefox -y"
	javaworkshop.vm.provision "shell", inline: "cinst google-chrome-x64 -y"	
	javaworkshop.vm.provision "shell", inline: "cinst phantomjs -y"	
	javaworkshop.vm.provision "shell", inline: "cinst sourcetree -y"
	javaworkshop.vm.provision "shell", inline: "cinst eclipse -y"
	javaworkshop.vm.provision "shell", inline: "cinst conemu -y"
	javaworkshop.vm.provision "shell", inline: "cinst atom -y"
	javaworkshop.vm.provision "shell", inline: $provision
  end
$provision = <<provision
cd C:/TeamCity/bin/
START startup.bat
cd ~
provision
 end