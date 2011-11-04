Vagrant commands
==============

### Create a box from a VirtualBox system (output is a package.box file)
vagrant package --base VirtualBoxSystemName

### Import that box
vagrant box add vagrantSystemName package.box

### Remove a box
vagrant box remove vagrantSystemName

### Init a system (output is a Vagrantfile)
vagrant init vagrantSystemName

### Commands on a system
vagrant up|halt|destroy
