Update the task to use the "apt" module to install all required packages. The list of packages to be installed are given below. Remember to use loop (with_items) to install all packages in one task: 

        - python 
        - python-setuptools 
        - python-dev 
        - build-essential 
        - python-pip 
        - python-mysqldb 
Documentation: Refer to apt module - https://docs.ansible.com/ansible/latest/collections/ansible/builtin/apt_module.html
