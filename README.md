Haiku-OS Dev environment
----------
This recipe is an easy to create a development environment for Haiku-OS in MacOS. 

Why?
----------
because when you try to build Haiku-OS on MacOS you face two main problems:

* APFS / HFS+ is a non case-sensitive Filesystem by default ands the Haiku-OS build system depends on a case-sensitive filesystem, So you need to create a case-sensitive partition on Disk and build everything there.
* LLVM on Mac has some serious bugs when you try to compile Haiku source code

Requirements (dependencies)
------------
* Red Hat's Ansible on guest
* HashiCorp's Vagrant
    * vagrant-vbguest plugin

Installation
------------

clone this repo and install the dependencies.

If you have Homebrew you can run the following commands to install all the dependencies:

- `brew install vagrant`
- `brew install ansible`

and install:

- MacFUSE
- SSHFS complement
- Follow instructions to intall on recent MacOS

and the following vagrant plugins:

- `vagrant plugin install vagrant-vbguest`
- `vagrant plugin install vagrant-sshfs`
- `vagrant plugin install vagrant-ansible-local`

This installation is based on Rocky Linux 9 and build the x86-64 Haiku image

The current recipe shares the content of `/home/vagrant/` (where resides Haiku Buildtools and Haiku Source code tree) and mounts it in a directory named `haiku` one level up from this directory (`../haiku`). If for some reason the directory is not mounted when you run the vm, you can init manually the mount procedure using the command `vagrant sshfs`

Running the environment
------------
to run this recipe you only need to invoke `vagrant up` from this directory, and everything will build up automatically. The process should run for a couple of hours to complete.

When the process is complete you only need to run `vagrant ssh` ro access the vm to build Haiku. when you enter the vm there is 3 directories in the default folder.

* haiku : this directory contaimns all the source code for Haiku-OS
* buildtools: this directory contains the necesary tools to build Haiku
* generated.x86_64: Here resides the binary executables or the resulting ISO.

Warning
----------
To turn off the virtual machine do NOT use `vagrant destroy`, unless you want to lose permanently any changes have you made to the haiku source code or the buildtools. 

To turn on/off the Image properly, you can use `vagrant suspend` and `vagrant resume`.

TODO:
-----------
- Migrate the ansible playbook to role
- Add ARM architectecture to Ansible Playbook

Caveats:
-----------
- There is weird bvug that doesn't permit log into the box using `vagrant ssh`
