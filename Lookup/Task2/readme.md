Introduction: Let us attempt the same operation if the credential file were to be in ini format. In the given playbook, the password for the host web_server is hardcoded into a variable ansible_ssh_pass. 

Task: Replace the Ansible Password field to use "lookup" plugin to lookup a "ini" file, the file is "credentials.ini" and the value to lookup is "password" and the section is "web_server".

[ini lookup](https://docs.ansible.com/projects/ansible/latest/collections/ansible/builtin/ini_lookup.html)
