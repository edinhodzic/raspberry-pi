# Prerequisites
  
- Raspberry Pi with:
  - Raspberry Pi OS installed
  - a connection to the local network

- A computer to be used as an Ansible [control node](https://docs.ansible.com/ansible/latest/network/getting_started/basic_concepts.html#control-node) with:
  - Ansible installed - see [Ansible's documentation](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)
  - an SSH key - preferred way for Ansible control notes to connect to [managed nodes](https://docs.ansible.com/ansible/latest/network/getting_started/basic_concepts.html#managed-nodes)
  
- Control node SSH key copied to managed node:
  ```shell script
  bash-3.2$ ssh-copy-id -i ~/.ssh/id_rsa.pub pi@raspberrypi.local
  /usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/Users/edin/.ssh/id_rsa.pub"
  The authenticity of host 'raspberrypi.local (2a01:4b00:f804:6400:8288:b7ae:4328:c784)' can't be established.
  ECDSA key fingerprint is SHA256:VFKSk5pLvHvOmzG8nBJ5rXPdtEpK0X9WiNm2OwNjA1Q.
  Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
  /usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
  /usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
  pi@raspberrypi.local's password:
  
  Number of key(s) added:        1
  
  Now try logging into the machine, with:   "ssh 'pi@raspberrypi.local'"
  and check to make sure that only the key(s) you wanted were added.
  
  bash-3.2$
  ```  

# Usage

Run the Ansible playbook to set everything up:  
```shell script  
bash-3.2$ ansible-playbook -i hosts pihole-playbook.yml -vv
ansible-playbook 2.10.3
  config file = /Users/edin/.ansible.cfg
  configured module search path = ['/Users/edin/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/local/Cellar/ansible/2.10.3/libexec/lib/python3.9/site-packages/ansible
  executable location = /usr/local/bin/ansible-playbook
  python version = 3.9.0 (default, Oct 27 2020, 14:15:17) [Clang 12.0.0 (clang-1200.0.32.21)]
  ...
```

# Not automated

On the router:
- static IP for RasPi
- primary DNS set to RasPi IP
