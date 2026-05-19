# Ansible

### Tasks vs Roles
The primary difference is organization and reusability: tasks are the individual, sequential execution steps written directly inside a playbook, while roles are packaged, self-contained bundles of tasks, variables, and templates that can be easily shared across different playbooks.

Think of tasks as writing code inline in a single script, and roles as creating a clean, modular library function.

use ansible-galaxy init role_name command to create the default role structure (folders).

### Asynchronous
By default, Ansible runs synchronously, meaning it connects to a host, executes a task, and blocks the entire playbook from moving forward until that task completes.Asynchronous mode breaks this blocking behavior. It allows a task to fire off a long-running process in the background, freeing Ansible to either check on it periodically or immediately proceed to the next task in the playbook

Why Use Asynchronous Execution?
- Avoid SSH Timeouts: Long processes like database migrations, heavy package compilations, or system reboots can exceed standard SSH timeout limits and crash the run.
Use this when you want to block the playbook until the task is complete, but you know the task takes a long time and might drop the SSH connection
- Parallel Task Execution: You can kick off time-consuming operations on multiple hosts simultaneously instead of waiting for each one to finish sequentially.
- Fire-and-Forget Actions: You can trigger background daemons or scripts (like a Flask server bootstrap) and completely detach Ansible from the lifecycle of that process.
Setting poll: 0 tells Ansible to start the command and immediately move to the very next task without waiting for a response. This is ideal for background services.

The Two Core KeywordsTo make a task asynchronous, you append two specific keywords to the task definition:
- async: The maximum amount of time (in seconds) that Ansible will allow the task to run. If the job takes longer than this value, Ansible terminates it.
- poll: How often (in seconds) Ansible checks back with the host to see if the job is finished.
