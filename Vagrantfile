Vagrant.configure("2") do |config|

  config.vm.define "ansiblectl", primary: true do |ansiblectl|
    ansiblectl.vm.box = "http://dtl24vuvdev86.ca.bestbuy.com/downloads/vagrant/ansible/bby.goldenbase.ansible_ABA25FC1-13B7-4A02-9C5A-3DF322369412-2019-06-10.box"
    ansiblectl.vm.network "private_network", ip: "172.28.128.10"
    ansiblectl.vm.synced_folder "./", "/vagrant", type: "nfs"
    ansiblectl.vm.hostname = "ansiblectl"

    ansiblectl.vm.provider "virtualbox" do |vb|
      vb.gui = false
      vb.memory = "2048"
    end

    ansiblectl.vm.provision "shell", inline: <<-SHELL
      # Install Ansible
      yum install epel-release -y
      yum install ansible -y
      yum update ansible -y
    SHELL

    ansiblectl.vm.provision "ansible_local" do |ansible|
        ansible.playbook = "/vagrant/site.yml"
    end
  end
end