### Error Handling in Ansible

Ansible provides built-in mechanisms to intercept failures, clean up corrupted states, and keep your automation running smoothly instead of immediately crashing.
By default, if a task fails on a host, Ansible stops executing all subsequent tasks for that specific host. 

You can override and manage this behavior using four primary patterns:

1. Blocks, Rescue, and Always (Try/Catch Logic)This is the standard structural approach for logical grouping. You group your primary execution tasks inside a block. If any task inside that block fails, Ansible stops that block and shifts down to execute the tasks inside the rescue section.
block: Contains the tasks you want to run.rescue: Runs only if a task inside the block section triggers a failure.always: Runs no matter what happens (regardless of success or failure in the previous blocks).

2. Ignoring Task Failures (ignore_errors)If a task failure is expected or non-critical (like cleaning up a file that might not exist), you can instruct Ansible to log the failure but continue processing the playbook.

3. Redefining Success and Failure (failed_when)Sometimes custom shell scripts exit with a non-zero status code even if they executed successfully, or they return 0 but print an error message to the console. You can use failed_when to explicitly dictate what a real failure means.

4. Controlling Host Eviction (any_errors_fatal)By default, if Host A fails a task, Host B and Host C will keep running the rest of the playbook. In high-risk environments (like updating a clustered database), you might want the entire play to abort instantly if even a single node experiences a failure.

#### Ansible Error Handling Cheat Sheet


| Keyword | Use Case | Description |
| :--- | :--- | :--- |
| **`block`** | Group primary tasks | Bundles standard execution steps together under a single logical unit. |
| **`rescue`** | Trigger rollbacks | Executes recovery tasks *only* if a task inside the paired `block` fails. |
| **`always`** | Force cleanup actions | Runs structural teardown steps regardless of previous task success or failure. |
| **`ignore_errors`** | Bypass non-critical faults | Keeps the playbook running on a host even if that specific task throws an error. |
| **`failed_when`** | Custom failure conditions | Overrides default module logic to fail based on specific text logs or exit codes. |
| **`changed_when`** | Custom change tracking | Overrides reporting status so scripts don't always falsely report a system change. |
| **`any_errors_fatal`** | Global emergency stop | Aborts the entire playbook run instantly if even a single host encounters a failure. |
| **`max_fail_percentage`** | Batch failure thresholds | Aborts rolling deployments if failures exceed a set percentage of the batch size. |

