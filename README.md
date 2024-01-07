# Vagrant Templates

The point of this repository is to hold `Vagrantfile` templates that I use as starting points for self-contained development/testing environments.

These are not minimal templates. They include configuration tweaks for common issues that I run into, and provisioning scripts that install a few extra packages and customize the environment a bit. Check the `Vagrantfile` and the `vagrant/provision.sh` scripts as needed

## Use Cases 
* testing/development work with different linux environments
* dev environment app testing 
* yor own personal use

## Dependencies

You'll need [VirtualBox](https://www.virtualbox.org/) and [Vagrant](https://www.vagrantup.com/) installed locally.

Some templates may ask to install the `vagrant-vbguest` plugin (to share folders with the host) on `vagrant up` if they need it.

### Host-Only Networking
Starting with version 6.1.28, VirtualBox restricts the address ranges usable in [host-only networks](https://www.virtualbox.org/manual/ch06.html#network_hostonly) which causes `vagrant up` to fail as it tries to create an host-only network using a disallowed address range.

To work around this, the templates in this repository force `vagrant up` to use a host network called `vboxnet0` **which must be created beforehand**. Go to `File -> Host Network Manager` in VirtualBox and create the `vboxnet0` network if it doesn't already exist, also making sure it has the DHCP server enabled (default).
