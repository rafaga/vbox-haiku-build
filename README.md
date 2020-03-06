Haiku-OS Dev environment
-----------
I made this to make an easy and hassle-free development environment in MacOS. because when you try to build Haiku-OS on MacOS you face two main problems:

* Due to the fact that APFS / HFS+ is a non case-sensitive Filesystem by default, you need to create a case-sensitive partition on Disk and build everything there
* llvm sometimes has serious bugs when you try to compile Haiku soruce code

Due to this I have made this recipe

Requirements (dependencies)
------------
* Red Hat's Ansible
* HashiCorp's Vagrant
    * vagrant-sshfs plugin
    * vagrant-vbguest plugin
* osxFUSE - to mount sshfs on File system
* sshfs - to mount sshfs on File system

Instalation
------------

If you have Homebrew you can run the following

brew install vagrant
brew install ansible
brew install sshfs
vagrant install vagrant-sshfs
vagrant install vagrant-vbguest

This installation is based on centOS 7 and build the x86-64 Haiku image

Caveats
------------
Jam is installed in /usr/local/bin, so to run the Haiku build you need to execute /usr/local/bin/jam -q @nigthly-raw.