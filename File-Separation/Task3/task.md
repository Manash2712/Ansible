Do the same for all the tasks under web application deployment.

Move the below tasks to the new file and add include statement in the main playbook to include the file "tasks/deploy_web.yml"

- name: Install Python Flask dependencies
- name: Copy web-server code
- name: Start web-application
