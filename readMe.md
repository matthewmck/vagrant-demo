# Vagrant Box Notes

## Command Cheatsheet
```
vagrant up - init the vagrant box

vagrant suspend - shuts down the vagrant box

vagrant resume - starts up the vagrant box

vagrant reload - when making changes to the config files you will need to reload

vagrant ssh - allows you to ssh into your vagrant box. This is preconfigured for you so no setup is required. type exit to exit out

vagrant status - tells you the status of your vagrant box

vagrant destroy - deletes the vagrant box
```

## Install Guide
### Step 1: Install Vagrant box
visit [Vagrant](https://www.vagrantup.com/) and download the latest version. 

### Step 2: Create new dir for vagrant box
```
mkdir myVagrantBox
cd myVagrantBox
```
### Step 3: Install the environment you want from the public Vagrant box catalog
visit [https://app.vagrantup.com/boxes/search](https://app.vagrantup.com/boxes/search) to see the entire list of available boxs. when you find the box you want install it with the following command:
```
vagrant init ubuntu/trusty64
```

### Step 4: Setup the vagrantfile
The imporant parts of the vagrantfile are:
* config.vm.box - operating system
* config.vm.provider - virtual box
* config.vm.network - how your host sees your box
* config.vm.synced_folder - How you access files from your computer
* config.vm.provision - what we want to setup (tech stack)

#### config.vm.provider
uncomment the provider and delete everything inside, it should look like this when done:
```
# Provider Settings
config.vm.provider "virtualbox" do |vb|

end
```
Additionally, you can configure certain specs for the virtual box:
```
  # Provider Settings
  config.vm.provider "virtualbox" do |vb|
    vb.memory = 2048
    vb.cpus = 4
  end
```

#### config.vm.network
uncomment out whichever outcome your looking for
* port forward will forward port 80 to whichever port you specifiy to your host
* private network will create a ip address that only you can see

#### config.vm.synced_folder
* 1st param is the folder on host relative to the vagrant file
* 2nd param is the folder within the vm

#### config.vm.provision
This contains all of the commands to run when you init the vagrant box

### Step 5: Run the vagrantfile
```
vagrant up
```