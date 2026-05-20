Introduction: We have added a new task at the end to send a notification email, once all tasks are complete. 
However, the SMTP server is not very stable and these emails are not critical. We would like Ansible to ignore even if the email task fails 

Task: Set the ignore_errors option on the mail task to "yes" to ignore errors.
