# -*- mode: ruby -*-
# vi: set ft=ruby :

# Define the Vagrant environment
Vagrant.configure("2") do |config|

  # Using VMware Workstation provider
  config.vm.provider "vmware_workstation" do |v|
    v.vmx["numvcpus"] = "2" # Number of CPUs for each VM
    v.vmx["memsize"] = "2048" # Memory size for each VM in MB
  end

  # Create the first VM, which will be the "master" node
  config.vm.define "master" do |master|
    master.vm.box = "bento/ubuntu-22.04"
    master.vm.hostname = "master"
    master.vm.network "private_network", ip: "10.10.10.#{conf["ip"]}"
    master.vm.provider "vmware_workstation" do |v|
      v.vmx["displayName"] = "Master"
    end
  end

  # Create three additional VMs
  (1..3).each do |i|
    config.vm.define "node#{i}" do |node|
      node.vm.box = "bento/ubuntu-22.04"
      node.vm.hostname = "node#{i}"
      node.vm.network "private_network", ip: "10.10.10.1#{i+1}"
      node.vm.provider "vmware_workstation" do |v|
        v.vmx["displayName"] = "Node#{i}"
      end
    end
  end

end
