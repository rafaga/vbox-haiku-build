Haiku-OS Dev environment
----------
This recipe is an easy to create a development environment for Haiku-OS in MacOS. 

Why?
----------
because when you try to build Haiku-OS on MacOS you face two main problems:

* APFS / HFS+ is a non case-sensitive Filesystem by default ands the Haiku-OS build system depends on a case-sensitive filesystem, So you need to create a case-sensitive partition on Disk and build everything there.
* LLVM on Mac has some serious bugs when you try to compile Haiku soruce code

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

Create here a directory named home, to access the Haiku Buildtools and Haiku Source code tree. This recipe will try to mount a sshfs on the 'home' directory. So you can edit the files easily.

Warning
----------
Do not use vagrant destroy, unless you want to lose permanently any changes  made to the haiku source code or the buildtools. To turn on/off the Image correctly, you can use vagrant suspend and vagrant resume.




