# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"


Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

   config.vm.define "kubemaster" do |kubemaster|
   kubemaster.vm.box = "centos/7"
   kubemaster.vm.provision "shell", path: "check_key.sh"
   kubemaster.vm.provision "shell", :path => "swapoff.sh"
   kubemaster.vm.provision "shell", :path => "k8s_docker_install.sh"
   kubemaster.vm.provision "shell", :path => "k8s_install.sh"
   kubemaster.vm.provision "shell", :path => "kubeadm.sh"
   kubemaster.vm.network "private_network", ip:"10.1.0.2"
   kubemaster.vm.host_name = "kubemaster"
     kubemaster.vm.provider :libvirt do |lv|
      #Virtualbox
      #vb.customize ["modifyvm", :id, "--memory", "2048"]
      #vb.customize ["modifyvm", :id, "--cpus", "2"]

      #Libvirt
      lv.cpus = 2
      lv.memory = 2048
     end
   end

   config.vm.define "kubeworker1" do |kubeworker1|
   kubeworker1.vm.box = "centos/7"
   kubeworker1.vm.provision "shell", path: "check_key.sh"
   kubeworker1.vm.provision "shell", :path => "swapoff.sh"
   kubeworker1.vm.provision "shell", :path => "k8s_docker_install.sh"
   kubeworker1.vm.provision "shell", :path => "k8s_install.sh"
   kubeworker1.vm.provision "shell", :path => "admjoin.sh"
   kubeworker1.vm.network "private_network", ip:"10.1.0.3"
   kubeworker1.vm.host_name = "kubeworker1"
     kubeworker1.vm.provider :libvirt do |vb|
      vb.memory = 1024
     end
   end

   
   config.vm.define "kubeworker2" do |kubeworker2|
   kubeworker2.vm.box = "centos/7"
   #kubeworker2.vm.provision "shell", inline: "cat /vagrant/pub_key >> /home/vagrant/.ssh/authorized_keys"
   kubeworker2.vm.provision "shell", path: "check_key.sh"
   kubeworker2.vm.provision "shell", :path => "swapoff.sh"
   kubeworker2.vm.provision "shell", :path => "k8s_docker_install.sh"
   kubeworker2.vm.provision "shell", :path => "k8s_install.sh"
   kubeworker2.vm.provision "shell", :path => "admjoin.sh"
   kubeworker2.vm.network "private_network", ip:"10.1.0.4"
   kubeworker2.vm.host_name = "kubeworker2"
     kubeworker2.vm.provider :libvirt do |vb|
      vb.memory = 1024
     end
   end

 
   config.vm.define "k8snfs" do |k8snfs|
   k8snfs.vm.box = "centos/7"
   #k8snfs.vm.provision "shell", inline: "cat /vagrant/pub_key >> /home/vagrant/.ssh/authorized_keys"
   k8snfs.vm.provision "shell", path: "check_key.sh"
   #k8snfs.vm.provision "shell", :path => "swapoff.sh"
   #k8snfs.vm.provision "shell", :path => "k8s_docker_install.sh"
   #k8snfs.vm.provision "shell", :path => "k8s_install.sh"
   #k8snfs.vm.provision "shell", :path => "admjoin.sh"
   k8snfs.vm.network "private_network", ip:"10.1.0.6"
   k8snfs.vm.host_name = "k8snfs"
     k8snfs.vm.provider :libvirt do |vb|
      vb.memory = 512
      vb.storage :file, :size => '10G'
      #libvirt.storage :file, :size => '20G'
     end
   end

#   config.vm.define "kubeworker3" do |kubeworker3|
#   kubeworker3.vm.box = "centos/7"
#   kubeworker3.vm.provision "shell", path: "check_key.sh"
#   kubeworker3.vm.provision "shell", :path => "swapoff.sh"
#   kubeworker3.vm.provision "shell", :path => "k8s_docker_install.sh"
#   kubeworker3.vm.provision "shell", :path => "k8s_install.sh"
#   kubeworker3.vm.provision "shell", :path => "admjoin.sh"
#   kubeworker3.vm.network "private_network", ip:"10.1.0.5"
#   kubeworker3.vm.host_name = "kubeworker3"
#     kubeworker3.vm.provider :libvirt do |vb|
#      vb.memory = 1024
#     end
#   end
end
