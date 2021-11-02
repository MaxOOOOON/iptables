# -*- mode: ruby -*-
# vim: set ft=ruby :


MACHINES = {
   :inetRouter => {
        :box_name => "centos/7",
        :memory => 512,
        :net => [
                   {ip: '192.168.255.1', adapter: 2, netmask: "255.255.255.248", virtualbox__intnet: "net-route"},
                ]
  },
  :centralRouter => {
        :box_name => "centos/7",
        :memory => 512,
        :net => [
                   {ip: '192.168.255.2', adapter: 2, netmask: "255.255.255.248", virtualbox__intnet: "net-route"},
                   {ip: '192.168.0.1', adapter: 3, netmask: "255.255.255.240", virtualbox__intnet: "dir-net"},
           
                ]
  },

  :centralServer => {
        :box_name => "centos/7",
        :memory => 512,
        :net => [
                   {ip: '192.168.0.2', adapter: 2, netmask: "255.255.255.240", virtualbox__intnet: "dir-net"},
                ]
  },


  :inetRouter2 => {
          :box_name => "centos/7",
          :net => [
                     {ip: '192.168.255.3', adapter: 2, netmask: "255.255.255.248", virtualbox__intnet: "net-route"},
                  ]
  },

}

Vagrant.configure("2") do |config|

    MACHINES.each do |boxname, boxconfig|

        config.vm.define boxname do |box|

            box.vm.box = boxconfig[:box_name]
            box.vm.host_name = boxname.to_s

            boxconfig[:net].each do |ipconf|
            box.vm.network "private_network", ipconf
            end
            box.vm.provider :virtualbox do |vb|
                    vb.customize ["modifyvm", :id, "--memory", "512"]
            end        

            case boxname.to_s
            when "inetRouter2"
            box.vm.network "forwarded_port", guest: 8080, host: 8080
           
            end
            box.vm.provision :ansible do |ansible|
                ansible.playbook = "./playbook.yml"
                ansible.inventory_path = "./inventory.yml"
                # ansible.verbose = true
              end
            
            
        end
    end  
end