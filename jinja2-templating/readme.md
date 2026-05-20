# Jinja2 Templating Lecture Notes

Jinja2 templating is a powerful tool used in Ansible for generating dynamic content.

More Details: 
[Templating (Jinja2)](https://docs.ansible.com/projects/ansible/latest/playbook_guide/playbooks_templating.html)

## Key Concepts

1. **Basic Templating**
   - Templating allows for the creation of dynamic expressions rather than static text.
   - Variables are denoted using double curly brackets (e.g., `{{ variable_name }}`).

2. **Defining Variables**
   - It is essential to define variables before using them to avoid errors.
   - ```yaml
     vars:
       my_name: "Manash"
     ```
   - The debug module allows testing Jinja2 expressions:
     ```yaml
     - debug:
         msg: "Hello, my name is {{ my_name }}"
     ```

3. **Jinja2 Engine**
   - Jinja2 is a full-featured template engine utilized by Ansible for its templating needs.

4. **Filters**
   - Filters modify the output of variables. Key filters include:
     - **Upper**: Converts a string to uppercase.
     - **Lower**: Converts a string to lowercase.
     - **Title**: Capitalizes the first letter of each word.
     - **Replace**: Replaces specified parts of the string.
     - **Default**: Provides a fallback value for undefined variables.
     - - **Upper**: Convert to uppercase.
       ```yaml
       msg: "{{ my_name | upper }}"
       ```
     - **Lower**: Convert to lowercase.
       ```yaml
       msg: "{{ my_name | lower }}"
       ```
     - **Replace**: Replace part of a string.
       ```yaml
       msg: "{{ my_name | replace('Manas', 'Manash') }}"
       ```
     - Use the default filter to avoid errors if a variable is undefined:
       ```yaml
       msg: "{{ my_name | default('Guest') }}"
       ```

5. **List and Set Filters**
   - Filters such as Min, Max, Unique, Union, and Intersect are used for operating on arrays.

6. **Random and Join Filters**
   - **Random**: Generates a random number.
   - **Join**: Combines elements of an array into a string with a specified separator.

7. **File-related Filters**
   - Filters like Base Name and win_splitdrive help extract specific components from file paths, demonstrating differences between Unix and Windows formats.

8. **Chaining Filters**
   - The concept of chaining multiple filters together allows for more complex data manipulation.
     ```yaml
     msg: "{{ my_name | upper | replace('MANAS', 'MANASH') }}"
     ```
     
