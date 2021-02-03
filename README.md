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
                                                                                              
                                                                                              

<p class="has-line-data" data-line-start="0" data-line-end="1">The “playbook” for Ansible to configure security bulk ports change on esxi hosts with NVDS.</p>
<p class="has-line-data" data-line-start="2" data-line-end="3">for NSX-T 2.5,3.0,3.1</p>
<h3 class="code-line" data-line-start=4 data-line-end=5 ><a id="_4"></a></h3>
<p class="has-line-data" data-line-start="5" data-line-end="7">Requirements:<br>
Ansible 2.6+</p>
<h3 class="code-line" data-line-start=8 data-line-end=9 ><a id="_8"></a></h3>
<p class="has-line-data" data-line-start="9" data-line-end="10">How to use it.</p>
<ol>
<li class="has-line-data" data-line-start="11" data-line-end="25">
<p class="has-line-data" data-line-start="11" data-line-end="17">Change configuration in “hosts” file:<br>
[esxi]<br>
192.168.201.11   ansible_user=root     ### esxi host ###<br>
192.168.201.12   ansible_user=root     ### esxi host ###<br>
192.168.201.13   ansible_user=root     ### esxi host ###<br>
192.168.201.14   ansible_user=root     ### esxi host ###</p>
<p class="has-line-data" data-line-start="18" data-line-end="24">[esxi:vars]<br>
promisc=“false”<br>
forgesrc=“true”<br>
macchange=“true”<br>
write=“false”<br>
edge_name=192.168.201.33              ### part of VM-name, can use in extra-vars ###</p>
</li>
<li class="has-line-data" data-line-start="25" data-line-end="26">
<p class="has-line-data" data-line-start="25" data-line-end="26">execute one of the listed command:</p>
</li>
</ol>
<ul>
<li class="has-line-data" data-line-start="26" data-line-end="28">read current configuration.<br>
ansible-playbook check.yml -i hosts</li>
<li class="has-line-data" data-line-start="28" data-line-end="30">change configuration on ports.<br>
ansible-playbook check.yml -i hosts --extra-vars “write=true”</li>
<li class="has-line-data" data-line-start="30" data-line-end="32">change configuration on ports without using default values.<br>
ansible-playbook check.yml -i hosts --extra-vars “write=true macchange=true promisc=false forgesrc=false”</li>
</ul>
