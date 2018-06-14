# vagrant-ubuntu18.04-ri5cy

Vagrantfile for Ubuntu 18.04 with the gcc toolchain for the RI5CY small 4-stage RISC-V core.

## Installation

To provision a virtual machine with the Vagrantfile it is required to install *VirtualBox* and *vagrant*.

## Vagrant commands

### Basics

Run these commands in the folder where the *Vagrantfile* file is located.

Install or bring up vagrant controlled machine

```
$ vagrant up
```

Stop vagrant controlled machine

```
$ vagrant halt
```

Reprovision vagrant controlled machine

```
$ vagrant provision
```

Remove vagrant controlled machine

```
$ vagrant destroy
```

### Copy vagrant box

Compress vagrant box to a package.box file (default name) in the same folder

```
$ vagrant halt
$ vagrant package
```

Create a new VM from the new box file

```
$ vagrant init
```

Open the file and change the default boxname (which might be precise64) to something new, like “my-zend-framework-box“.
Uncomment and edit the default box location from
to the filepath of your package.box. 
Windows users need to write the path as given in the example.

```
$ config.vm.box = "my-zend-framework-box"

$ # config.vm.box_url = "http://domain.com/path/to/above.box"
$ config.vm.box_url = "file:///d:/folder/package.box"
```

```
$vagrant up
```

