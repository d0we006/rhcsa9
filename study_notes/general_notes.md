# Final preperation
## General Tips
### Order in which you work on the assignments: 

```
<1>1. Make sure that your server boots and you have root access to it.
<1>2. Configure networking in the way it is supposed to work.
<1>3. Configure any repositories that you need.
<1>4. Install and enable all services that need to be up and running at the end of the exam.
<1>5. Work on all storage-related tasks.
<1>6. Create all required user and group accounts.
<1>7. Set permissions.
<1>8. Make sure SELinux is working and configured as required.
<1>9. Work on everything else.
```

1. reboot
1.1 A successful reboot allows you to verify that everything is working up to the moment you have rebooted.
1.12 Before rebooting, remove the rhgb and quiet option from the GRUB boot loader => allows you to see what is actually happening and makes troubleshooting a lot easy.
1.13 Should at least reboot after working on all storage-related assignments.
1.2 Ensure that all the tasks are implemented with firewalld and SELinux enabled. Your server should be able to survive the reboot.
