               ___           ___           ___           ___           ___           ___              
              /\__\         /\  \         |\__\         /\  \         /\__\         |\__\             
             /::|  |       /::\  \        |:|  |       /::\  \       /:/  /         |:|  |            
            /:|:|  |      /:/\ \  \       |:|  |      /:/\:\  \     /:/  /          |:|  |            
           /:/|:|  |__   _\:\~\ \  \      |:|__|__   /:/  \:\  \   /:/  /  ___      |:|__|__          
          /:/ |:| /\__\ /\ \:\ \ \__\ ____/::::\__\ /:/__/_\:\__\ /:/__/  /\__\     /::::\__\         
          \/__|:|/:/  / \:\ \:\ \/__/ \::::/~~/~    \:\  /\ \/__/ \:\  \ /:/  /    /:/~~/~            
              |:/:/  /   \:\ \:\__\    ~~|:|~~|      \:\ \:\__\    \:\  /:/  /    /:/  /              
              |::/  /     \:\/:/  /      |:|  |       \:\/:/  /     \:\/:/  /     \/__/               
              /:/  /       \::/  /       |:|  |        \::/  /       \::/  /                          
              \/__/         \/__/         \|__|         \/__/         \/__/                           
                                                                                              
                                                                                              

The "playbook" for Ansible to configure security bulk ports change on esxi hosts with NVDS.

for NSX-T 2.5,3.0,3.1

###
Requirements:
Ansible 2.6+

###
How to use it.

1) Change configuration in "hosts" file:
[esxi]
192.168.201.11   ansible_user=root
192.168.201.12   ansible_user=root
192.168.201.13   ansible_user=root
192.168.201.14   ansible_user=root

[esxi:vars]
promisc="false"
forgesrc="true"
macchange="true"
write="false"
edge_name=192.168.201.33

2) execute next command:
  2a) read current configuration.
     ansible-playbook check.yml -i hosts
  2b) change configuration on ports.
     ansible-playbook check.yml -i hosts --extra-vars "write=true"
  2c) change configuration on ports without using default values.
     ansible-playbook check.yml -i hosts --extra-vars "write=true macchange=true promisc=false forgesrc=false"
