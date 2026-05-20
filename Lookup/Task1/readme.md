Introduction: We have moved the credentials for hosts out of the inventory file and moved into a separate csv file called credentials.csv. 
Check it out!  In the given playbook, the password for the host web_server is hard-coded into a variable ansible_ssh_pass.

Task:  Replace the Ansible Password field to use "lookup" plugin to lookup a "csvfile", the file is "credentials.csv" and the value to lookup is "web_server".

[CSV Lookup](https://docs.ansible.com/projects/ansible/latest/collections/ansible/builtin/csvfile_lookup.html)
