# -*- mode: ruby -*-
# vi: set ft=ruby :

project_dir = File.dirname(File.expand_path(__FILE__))


# Взяли ключик хоста, ещё пригодится
ssh_public_key = File.read(File.join(Dir.home, ".ssh", "id_rsa.pub"))

host_name = "opennebula-matryoshka"
host_ip = "192.168.56.112"
front_end_port = 80
vm_user = "vagrant"
remote_user_dir = "/home/vagrant"

# Пишем абсолютные пути для плейбуков, чтобы те не потеряли докер файлы.
# Ну и пользователя тоже запишем
File.write(
	"ansible-playbooks/config.yml", 
	"---\n
	project_dir: #{project_dir}\n
	vm_user: #{vm_user}"
)



VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
	config.vm.box = "generic/ubuntu2004"
	config.vm.hostname = host_name
	config.vm.network :private_network, ip: host_ip
	config.vm.network :forwarded_port, host: front_end_port, guest: 80
	config.vm.provider "virtualbox" do |vbox|
		vbox.name = host_name
		vbox.memory = 4096
		vbox.cpus = 2

	# Вот и пользователь подъехал
	config.ssh.username = "#{vm_user}"
  	config.ssh.password = "xxXX1234"  # Позже вынести всё в отдельные файлики

	# Закинули ключик на тачку
	config.vm.provision "shell", inline: <<-SHELL
		echo "#{ssh_public_key}" >> "#{remote_user_dir}/.ssh/authorized_keys"
	SHELL

	# Запустили основной сценарий
	config.vm.provision :ansible do |ansible|
		ansible.playbook = "#{project_dir}/opennebula-matryoshka.yml"
	end
	#config.vm.provision "shell", path: "#{dependencies}/dependencies.sh"
end
