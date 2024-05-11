Vagrant scripts to deploy websites and databases

Dev-Ops

1. Open Vagrant account
2. Download VMFusion Public Tech 21H1 - https://customerconnect.vmware.com/downloads/get-download?downloadGroup=FUS-PUBTP-2021H1
3. Install VMWare
4. Run - ln -s /Applications/VMWare\ Fusion\ Tech\ Preview.app /Applications/VMWare\ Fusion.app
5. Download vagrant utility - https://developer.hashicorp.com/vagrant/install/vmware
6. Once downloaded, install
7. Install Vagrant plug-in - run in command = vagrant plugin install vagrant-vmware-desktop --plugin-version=3.0.1
8. Check your settings:
    1. Go to System Settings
    2. Privacy & security
    3. Accessibility
    4. Check that VMWare Fusion Tech Preview is listed and on. If not, add by clicking the plus sign
9. Change directory to Desktop and Create 1 folder on the desktop by running the command:
    1. mkdir vms
        1. Create 2 folders in vms by running the command:
    2. mkdir ubuntu
    3. mkdir fedora
10. Change directory into vms/ubuntu
11. Create a file in ubuntu called Vagrantfile by running the command:
    1. vim Vagrantfile
        1. Once the editor opens, press i for insert mode
        2. Past the following content in the file:

Vagrant.configure("2") do |config| 
config.vm.box = "spox/ubuntu-arm" 
config.vm.box_version = "1.0.0"
config.vm.network "private_network", ip: "192.168.56.11"
config.vm.provider "vmware_desktop" do |vmware|
		vmware.gui = true
		vmware.allowlist_verified = true
	end
end

            * Press :wq to exit the file

12. Go to https://app.vagrantup.com/boxes/search
    1. Filter by provider = VM Desktop
    2. In the search bar, type arm
        1. This is where you can find images. Our file however specify we are looking for “spot/ubuntu and the version number
13. Run the following command within the Ubuntu folder:
    1. vagrant up
        1. This will download the image and launch it
        2. Once completed, use the following command:
            1. vagrant ssh
14. To stop the vm, type the following:
    1. vagrant halt
15. To check the current status of the machine:
    1. vagrant status
        1. Either it is running or stopped