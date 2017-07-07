# metomi-vms - Cylc Tutorial Branch

Vagrant virtual machines with [FCM](http://metomi.github.io/fcm/doc/) + [Rose](http://metomi.github.io/rose/doc/rose.html) + [Cylc](http://cylc.github.io/cylc/) installed.

**This is the Cylc Tutorial Branch of Hilary Oliver's metomi VMs repository fork.**
If you are not looking for the Cylc Tutorial go to https://github.com/metomi/metomi-vms 

Table of contents:
* [Software Requirements](#software-requirements)
* [Setting up the Virtual Machine](#setting-up-the-default-virtual-machine)
* [Running the Virtual Machine](#using-the-default-virtual-machine)
* [Etc](#etc)


## Software Requirements

In order to use this virtual machine (VM) you must first install:
 * [VirtualBox](https://www.virtualbox.org/), software that enables running of virtual machines (version 5.1.6 or later required).
 * [Vagrant](https://www.vagrantup.com/), software that allows easy configuration of virtual machines (version 1.9.1 or later required).

These applications provide point-and-click installers for Windows and can usually be installed via the package manager on Linux systems.

## Setting up the Virtual Machine

After you have installed VirtualBox and Vagrant, download the metomi VM setup files from this GitHub URL:
 * zip (Windows):
    https://github.com/hjoliver/metomi-vms/archive/cylc-tutorial.zip
 * tar.gz (Linux):
    https://github.com/hjoliver/metomi-vms/archive/cylc-tutorial.tar.gz

Extract the files; they will be in a folder called `metomi-vms-cylc-tutorial`. The VM is based on Ubuntu 16.04.
If necessary you can customise it by editing the file `Vagrantfile` in this folder, as follows:
* By default the VM will be built with support for accessing the Met Office Science Repository Service.
  If you don't want this (or don't have an account) then remove `mosrs` from the `args` in the `config.vm.provision` line.
* By default the VM is configured with 1 GB memory and 2 CPUs.
  You may want to increase these if your host machine is powerful enough.

See the [Vagrant documentation](https://docs.vagrantup.com/v2/virtualbox/configuration.html) for more details on configuration options.

Before proceeding you need to be running a terminal with your current directory
set to `metomi-vms-cylc-tutorial` (i.e. inside your extracted archive).
* Windows users: navigate here with File Explorer and use
  `Shift-> Right Mouse Click -> Open command window here`.

Now, in this folder run the command `vagrant up` to build and launch the VM.
*This will download a base VM and then install lots of additional software, so
it can take a long time (depending on the speed of your internet connection).*
Note that a login screen will appear in a separate window but you will not be
able to login at this stage. Once the installation is complete the VM will
shutdown.

## Running the Virtual Machine

Run the command `vagrant up` (from a terminal within the same folder again) to
launch the VM.  A window should pop up containing a lightweight Linux desktop
environment ([LXDE](http://lxde.org/)) with a terminal already opened.

Alternatively, start up Virtual Box Manager (called `Oracle VM VirtualBox` in
the Windows menu), select the *metomi-vm-ubuntu-1604-cylc-tutorial* VM and run
it.

Either way, __inside the VM your Linux username and password are both
vagrant__. You have sudo access to the system and can install additional
software via the Ubuntu package manager, e.g. `sudo apt-get install htop`.

If your VM includes support for the Met Office Science Repository Service then
you will be prompted for your password (and also your user name the first time
you use the VM).
If you get your MOSRS username or password wrong and Subversion fails to
connect, just run `mosrs-cache-password` to try again.

You should find the tutorial PDF document on the desktop
(`$HOME/Desktop/cylc-tutorial.pdf`) and the tutorial example suites under
`$HOME/cylc-tutorial/`

Cylc and Rose should work already:
```
vagrant@vagrant:~$ cylc --version
7.4.0
```

The VM is configured with a local [Rose suite repository](http://metomi.github.io/rose/doc/rose-rug-introduction.html#suite-storage) and with the suite log viewer running under apache.

In addition to the aforementioned Cylc Tutorial you can follow the [Rose Brief
Tour](http://metomi.github.io/rose/doc/rose-rug-brief-tour.html) and other
tutorials in the [Rose User Guide](http://metomi.github.io/rose/doc/rose.html), and
the more basic tutorial section in the [Cylc User
Guide](https://cylc.github.io/cylc/documentation.html#the-cylc-user-guide).

To shutdown the VM you can use the "power button" at bottom right hand corner
of the Linux desktop, or you can issue the command `vagrant halt` from the
command window where you launched the VM.

## Etc

(For more on metomi VM options and usage, including disabling the desktop
environment if hosting the VM on a Mac or Linux system that already has an X
server running, see the README at the main fork:
https://github.com/metomi/metomi-vms)
