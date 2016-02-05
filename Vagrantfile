# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

    Vagrant.require_version ">= 1.7.2"

    # vagrant-omnibus: installs latest chef client
    config.omnibus.chef_version = :latest
    # vagrant-berkshelf: downloads cookbook dependencies
    config.berkshelf.enabled = true
    # forward ssh agent
    config.ssh.forward_agent = true

    # update hosts file
    if Vagrant.has_plugin?("vagrant-hostmanager")
        config.vm.hostname = "php-lamp"
        config.hostmanager.enabled = true
        config.hostmanager.manage_host = true
    end

    # cache stuff to make next provision faster
    if Vagrant.has_plugin?("vagrant-cachier")
        config.cache.scope = :box
    end

    if Vagrant.has_plugin?("vagrant-vbguest")
        # disable vbguest additions as the vbox already has it
        config.vbguest.auto_update = false
    end

    # map local project dir to apache doc root
    config.vm.synced_folder ".", "/var/www/html",
        id: "vagrant-root",
        create: true,
        owner: "root",
        group: "www-data",
        mount_options: ["dmode=775,fmode=774"]

    config.vm.box = "bento/ubuntu-15.04"
    config.vm.network :forwarded_port, guest: 80, host: 8080, auto_correct: true
    config.vm.network "forwarded_port", guest: 3306, host: 3306, auto_correct: true

    config.vm.provision "chef_solo" do |chef|

        chef.log_level = "info"
        chef.roles_path = "roles"
        chef.environments_path = "environments"

        chef.environment = "php-lamp-local"
        chef.add_role "php-lamp-developer"
    end

end
