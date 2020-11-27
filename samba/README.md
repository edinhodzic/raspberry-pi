# Motivation

Want to write some Python code to run on Pi but prefer to use tooling on my Mac.
Rather than copying files from the Mac to the Pi, a Samba share can be used to share part of the Pi's file system with the Mac.
Then I can write code on the Mac and run it on the Pi with no manual copying in between.
  
# Usage

Run the Ansible playbook to set everything up:  
```shell script  
bash-3.2$ ansible-playbook -i hosts samba-playbook.yml -vv
ansible-playbook 2.10.3
  config file = /Users/edin/.ansible.cfg
  configured module search path = ['/Users/edin/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/local/Cellar/ansible/2.10.3/libexec/lib/python3.9/site-packages/ansible
  executable location = /usr/local/bin/ansible-playbook
  python version = 3.9.0 (default, Oct 27 2020, 14:15:17) [Clang 12.0.0 (clang-1200.0.32.21)]
  ...
```

On the Mac:
- open Finder
- press shortcut &#8984;+<kbd>K</kbd>
- enter `smb://raspberrypi.local/share` as the server address
- enter `pi` as the user and omit the password
- anything created on the share can be seen by both Mac and ~~Cheese~~ Pi
- Bob's your uncle
