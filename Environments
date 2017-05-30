## Creating Virtual Machine

* Install [vagrant](https://www.vagrantup.com/downloads.html).
* Install [VirtualBox](https://www.virtualbox.org/wiki/Downloads) is a recommended provider.
  Other [virtual machine providers](https://docs.vagrantup.com/v2/providers/) do exist.

When you create a VM with vagrant, it will create a Vagrantfile in your current directory as well as a hidden directory (.vagrant).
Vagrant only allows one virtual machine configuration per directory. You will want to organize your VMs:

* `mkdir -p /boxes/workshop`; `cd /boxes/workshop`

Initialize a virtual machine. `ubuntu/trusty64` is one default image. A list of other virtual machine images can be found [here](https://atlas.hashicorp.com/boxes/search).

    vagrant init ubuntu/trusty64

Start up the virtual machine.

    vagrant up

Then    

    vagrant ssh

You should be able to connect to the machine.

#### Windows help

* If you're running Hyper-V and VirtualBox, and you're experiencing crashes when you try to start a VM, you may need to turn off Hyper-V (which exclusively locks use of CPU for virtualization).
* If you can't run vagrant ssh, Add `C:\Program Files\Git\usr\bin` to your PATH, which includes `ssh`.

## Vagrantfile

The Vagrantfile will contain some settings you can adjust for memory, networking, etc.
Two customizations you may consider making if working with your VM long-term:

* 1) Enable a synced folder. This will allow you to edit code/files from editors in your host OS.
* 2) Fix DNS to use the same as your host OS instead of its own.

```ruby
  # Important, you must run vagrant in an admin shell if you want symlinks to work correctly.
  # i.e., for npm install to work properly, you must have vagrant provision the machine in admin cmd prompt.
  config.vm.synced_folder "C:/dev", "/code"
  config.vm.synced_folder "C:/projects", "/projects"

  config.vm.provider :virtualbox do |vb|
     # fix crappy dns
     # https://serverfault.com/questions/453185/vagrant-virtualbox-dns-10-0-2-3-not-working
     vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
  end
```

## Virtualbox Networking

In virtualbox, VMs typically have [four ways](http://catlingmindswipe.blogspot.com/2012/06/how-to-virtualbox-networking-part-two.html) to set up the network:
- Network Address Translation (NAT), *which is the default*,
- Bridged,
- Internal network
- Host Only (Recommended).

Unlike the first virtual machine, you cannot use the default mode, because there will be no way for the workshop VM to talk to the node VM. Instead, you much choose between bridged or host-only.

Private networking (Host-only) is the recommended setting for Linux/Mac/Windows 10. **Bonus**: You can use hard-coded ip address in your scripts. Uncomment the following line in Vagrantfile:

```ruby
config.vm.network "private_network", ip: "192.168.33.10"
```

Then run, `vagrant reload`. 

## Doing it once again (Practice).

* Create a new VM with vagrant in /boxes/mysql.
* Enable private networking, but with a different ip address.
