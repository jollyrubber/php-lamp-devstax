#php-lamp-devstax

Linux/Apache/MySQL/PHP Development Stack built with Vagrant & Chef

## Install
- [ChefDK](https://downloads.chef.io/chef-dk/)
- [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
- [Vagrant](https://www.vagrantup.com/downloads.html)
- A Git client because Chef may be cloning remote repositories

Verify the ChefDK installation with
```shell
$ chef verify
```
### Vagrant Plugins
The following plugins are required
```shell
$ vagrant plugin install vagrant-berkshelf
$ vagrant plugin install vagrant-omnibus
```
The following plugins are recommended but not required
```shell
$ vagrant plugin install vagrant-hostmanager
$ vagrant plugin install vagrant-vbguest
$ vagrant plugin install vagrant-cachier
```

### Startup the Vagrant Box
Assuming you checked out this repository to /php-lamp-devstax
```shell
$ cd /php-lamp-devstax
$ vagrant up
```
