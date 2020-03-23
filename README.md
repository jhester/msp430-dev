MSP430 Development Environment with Vagrant
==============
MSP430 Development Environment using Vagrant built on Ubuntu 18 LTS, TI GCC for MSP430 v8.3.2.2. This VM supports compiling msp430 code only, you can take the compiled binary and use whatever method you like to burn the firmware to the MSP430: for example, [mspdebug](https://github.com/dlbeer/mspdebug).

Prerequisites
-------------
- Install [Vagrant](https://www.vagrantup.com/docs/installation/)
- Have a MSP430 Launchpad.

Usage
-----
- `$ vagrant up` creates the VM for the first time
- `$ vagrant ssh` lets you log into the VM
- see `vagrant -h` for info on how to suspend/shutdown/delete/etc the VM.
- The root folder(which has the Vagrantfile and example code) is accessible as `/vagrant`

### Compiling
A simple blink program is included in the repo along with an example `Makefile` with all usual flags set for size and speed. To make sure things work compile the code:


		$ make

	
Now you can install the code onto the connected MSP430FR5969 Launchpad in a separate terminal window, assuming you have mspdebug.


		$ mspdebug tilib "prog msp430fr5969.out" 

	
You should see some blinking, at this point.

### Adding your project repo
The `/vagrant` folder is shared between host and the VM. If you `git clone` anything to the main folder, you can have a workspace. For example within the vagrant box:

$ cd /vagrant
$ mkdir Repos
$ git clone [REPO_URL] [REPO_NAME]

The "Repos" directory is a shared directory between your vagrant box and your host computer. in the same folder as this README.md file.

### Using your favorite text editor
Since "Repos" directory is a shared directory between your vagrant box and your host computer, you do not have to change your workflow in any way. ONLY use the vagrant box to compile code.

Open your favorite text editor, IDE, or VIM on your HOST computer, and navigate to this repository, `msp430-vagrant/Repos` directory. You will see the recently added project repository. Edit code at will, and use the vagrant to compile.

