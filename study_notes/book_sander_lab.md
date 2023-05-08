## Part I: Performing Basic System Management Tasks

### Lab 1.1
- Repeat the procedure “Performing an Installation” to install one more server. Details about the additional configuration on this server follow in exercises in later chapters. For now, it is sufficient to ensure that the following conditions are met:
- Use the server name server2.example.com.
- Set the network configuration to obtain an IP address automatically.
- Install this server using the Minimal Installation pattern.

### Lab 2.1
- Modify your shell environment so that on every subshell that is started, a variable is set. The name of the variable should be COLOR, and the value should be set to red. Verify that it is working.
- Use the appropriate tools to find the command that you can use to change a user password. Do you need root permissions to use this command?
- From your home directory, type the command ls -al wergihl * and ensure that errors as well as regular output are redirected to a file with the name /tmp/lsoutput.

### Lab 3.1
- Log in as user student and use sudo -i to open a root shell. In the home directory of root, create one archive file that contains the contents of the /home directory and the /etc directory. Use the name /root/essentials.tar for the archive file.
- Copy this archive to the /tmp directory. Also create a hard link to this file in the / directory.
- Rename the file /essentials.tar to /archive.tar.
- Create a symbolic link in the home directory of the user root that refers to /archive.tar. Use the name link.tar for the symbolic link.
- Remove the file /archive.tar and see what happened to the symbolic link. Remove the symbolic link also.
- Compress the /root/essentials.tar file.

### Lab 4.1
- Describe two ways to show line 5 from the /etc/passwd file.
- How would you locate all text files on your server that contain the current IP address? Do you need a regular expression to do this?
- You have just used the sed command that replaces all occurrences of the text Administrator with root. Your Windows administrators do not like that very much. How do you revert?
- Assuming that in the ps aux command the fifth line contains information about memory utilization, how would you process the output of that command to show the process that has the heaviest memory utilization first in the results list?
- Which command enables you to filter the sixth column of ps aux output?
- How do you delete the sixth line from the file ~/myfile?

### Lab 5.2
- Set up SSH-based authentication. From server2, use SSH to connect to server1.
- Make sure that graphical applications are supported through the SSH session. Also set up key-based authentication so that no password has to be entered while connecting to the remote server.

### Lab 6.1
- Set up a shared group environment that meets the following requirements:
- Create two groups: sales and account.
- Create users joana, john, laura, and beatrix. Make sure they have their primary group set to a private group that has the name of the user.
- Make joanna and john members of the group sales, and laura and beatrix members of the group account.
- Set a password policy that requires users to change their password every 90 days.

### Lab 6.2
- Create a sudo configuration that allows user bill to manage user properties and passwords, but which does not allow this user to change the password for the root user.

### Lab 7.1
- Set up a shared group environment. If you haven’t created these directories in a previous exercise yet, create two directories: /data/account and /data/sales. Make the group sales the owner of the directory sales, and make the group account the owner of the directory account.
- Configure the permissions so that the user owner (which must be root) and group owner have full access to the directory. There should be no permissions assigned to the others entity.
- Ensure that all new files in both directories inherit the group owner of their respective directory. This means that all files that will be created in /data/sales will be owned by the group sales, and all files in /data/account will be owned by the group account.
- Ensure that users are only allowed to remove files of which they are the owner.

### Lab 8.1
- If you didn’t do so earlier, set up the first server to use the FQDN server1.example.com. Set up the second server to use server2.example.com.
- On server1.example.com, use nmtui and configure your primary network card to automatically get an IP address through DHCP. Also set a fixed IP address to 192.168.4.210. On server2, set the fixed IP address to 192.168.4.220.
- Make sure that from server1 you can ping server2, and vice versa.
- To allow you to access servers on the Internet, make sure that your local DHCP server provides the default router and DNS servers.
## Part II: Operating Running Systems

### Lab 9.1
- Copy some RPM files from the installation disk to the /myrepo directory. Make this directory a repository and make sure that your server is using this repository.
- List the repositories currently in use on your server.
- Search for the package that contains the cache-only DNS name server. Do not install it yet.
- Perform an extensive query of the package so that you know before you install it which files it contains, which dependencies it has, and where to find the documentation and configuration.
- Check whether the RPM package contains any scripts. You may download it, but you may not install it yet; you want to know which scripts are in a package before actually installing it, right?
- Install the package you found in step 3.
- Undo the installation.

### Lab 10.1
- Launch the command dd if=/dev/zero of=/dev/null three times as a background job.
- Increase the priority of one of these commands using the nice value -5. Change the priority of the same process again, but this time use the value -15. Observe the difference.
- Kill all the dd processes you just started.
- Ensure that tuned is installed and active, and set the throughput-performance profile.

### Lab 11.1
- Install the vsftpd and httpd services.
- Set the default systemctl editor to vim.
- Edit the httpd.service unit file such that starting httpd will always auto-start vsftpd. Edit the httpd service such that after failure it will automatically start again in 10 seconds.

### Lab 12.1
- Create a cron job that performs an update of all software on your computer every evening at 11 p.m.
- Schedule your machine to be rebooted at 3 a.m. tomorrow morning.
- Use a systemd timer to start the vsftpd service five minutes after your system has started.

### Lab 13.1
- Configure the journal to be persistent across system reboots.
- Make a configuration file that writes all messages with an info priority to the file /var/log/messages.info.
- Configure logrotate to keep ten old versions of log files.

### Lab 14.1
- Add two partitions to your server. Create both partitions with a size of 100 MiB. One of these partitions must be configured as swap space; the other partition must be formatted with an Ext4 file system.
- Configure your server to automatically mount these partitions. Mount the Ext4 partition on /mounts/data and mount the swap partition as swap space.
- Reboot your server and verify that all is mounted correctly. In case of problems, read Chapter 18, “Essential Troubleshooting Skills,” for tips on how to troubleshoot.

### Lab 15.1
- Create a 500-MB logical volume named lvgroup. Format it with the XFS file system and mount it persistently on /groups. Reboot your server to verify that the mount works.
- After rebooting, add another 250 MB to the lvgroup volume that you just created. Verify that the file system resizes as well while resizing the volume.
- Verify that the volume extension was successful.

### Lab 15.2
- Create a Stratis pool with a size of 5 GiB. In this pool, create two Stratis file systems and ensure that they are automatically mounted.
- Add an additional block device to the Stratis pool and verify that the size of the pool was successfully extended.
- Ensure that the new Stratis device is automatically mounted on the directory /stratis while rebooting.
## Part III: Performing Advanced System Administration Tasks

### Lab 16.1
- Find out whether a new version of the kernel is available. If so, install it and reboot your computer so that it is used.
- Use the appropriate command to show recent events that have been logged by the kernel.
- Locate the kernel module that is used by your network card. Find out whether it has options. Try loading one of these kernel module options manually; if that succeeds, take the required measures to load this option persistently.

### Lab 17.1
- Set the default target to multi-user.target.
- Reboot to verify this is working as expected.

### Lab 17.2
- Change your GRUB 2 boot configuration so that you will see boot messages upon startup.

### Lab 18.1
- Restart your server and change the root password from the appropriate troubleshooting mode.
- In /etc/fstab, change one of the device names so that on the next reboot the file system on it cannot be mounted. Restart and fix the issue that you encounter.
- Use a rescue disk to bring your server up in full troubleshooting mode from the rescue disk.
- Re-create the initramfs.

### Lab 19.1
- Write a script that works with arguments. If the argument one is used, the script should create a file named /tmp/one. If the argument two is used, the script should send a message containing the subject “two” to the root user.
- Write a countdown script. The script should use one argument (and not more than one). This argument specifies the number of minutes to count down. It should start with that number of minutes and count down second by second, writing the text “there are nn seconds remaining” at every iteration. Use sleep to define the seconds. When there is no more time left, the script should echo “time is over” and quit.
## Part IV: Managing Network Services

### Lab 20.1
- Configure your SSH server in such a way that inactive sessions will be kept open for at least one hour.
- Secure your SSH server so that it listens on port 2022 only and that only user lisa is allowed to log in.
- Test the settings from server2. Make sure that the firewall as well as SELinux are configured to support your settings.

### Lab 21.1
- Install the required packages that allow you to run a basic web server. Make sure that the web server process is started automatically when your server reboots. Do not use a virtual server.
- Use curl to make sure the web server presents a default page showing “Welcome to my web server.”
- Type dnf install httpd-manual to install the Apache documentation.
- Use a browser to test access to the /manual web page on your server.

### Lab 22.1
- Change the Apache document root to /web. In this directory, create a file with the name index.html and give it the content welcome to my web server. Restart the httpd process and try to access the web server. This will not work. Fix the problem.
- In the home directory of the user root, create a file with the name hosts and give it the following content:
- Click here to view code image
- 192.168.4.200 labipa.example.com
- 192.168.4.210 server1.example.com
- 192.168.4.220 server2.example.com
- Move the file to the /etc directory and do what is necessary to give this file the correct context.

### Lab 23.1
- Create a firewall configuration that allows access to the following services that may be running on your server:
- web
- ftp
- ssh
- Make sure the configuration is persistent and will be activated after a restart of your server.

### Lab 24.1
- Set up an NFS server that shares the /home directory on server2.
- Configure server1 to access the NFS-shared home directory using automount. You need to do this using wildcard automount.

### Lab 24.1
- Set up an NFS server that shares the /home directory on server2.
- Configure server1 to access the NFS-shared home directory using automount. You need to do this using wildcard automount.

### Lab 25.1
- Compare the current hardware time to the system time. If there is a difference, make sure to synchronize time.
- Set the time zone to correspond to the current time in Boston (USA East Coast).

### Lab 26.1
- Ensure that you have logged in to get access to the Red Hat container registries.
- Download the mariadb container image to the local computer.
- Start the mariadb container, meeting the following requirements:
- The container must be accessible at port 3206.
- The MYSQL_ROOT_PASSWORD must be set to “password”
- A database with the name mydb is created.
- A bind-mounted directory is accessible: the directory /opt/mariadb on the host must be mapped to /var/lib/mysql in the container.
- Configure systemd to automatically start the container as a user systemd unit upon (re)start of the computer.
