Vagrant.configure("2") do |config|
    N = 2
    (1..N).each do |vm_id|
        config.vm.define "vm#{vm_id}" do |VM|
            VM.vm.box = "centos/7"
            #VM.disksize.size = "40GB"
            VM.vm.hostname = "cm#{vm_id}"

            VM.vm.provision :shell, inline: "echo ready..."
        end
    end

    config.vm.define "vm0" do |VM|
        VM.vm.box = "centos/7"
        VM.vm.hostname = "cm#{vm_id}"

        VM.vm.provision :shell, inline: "echo ready..."

        VM.vm.provision :ansible_local do |ansible|
            ansible.limit = "all"
            ansible.playbook = "playbook.yml"
            #ansible.inventory_path = "hosts"
            ansible.galaxy_role_file = "requirements.yml"
            ansible.groups = {
                "docker_nodes" => ["vm[1:2]"],
                "docker_swarm_worker" => ["vm1"],
                "docker_swarm_manager"  => ["vm2"]
            }
        end
    end

#    config.vm.provision :ansible do |ansible|
#        # Disable default limit to connect to all the machines
#        ansible.limit = "all"
#        ansible.playbook = "playbook.yml"
#        #ansible.inventory_path = "hosts"
#        ansible.galaxy_role_file = "requirements.yml"
#    end

end
