## Part V: RHCSA 9 Practice Exams
### RHCSA Practice Exam A

#### General Notes
- Here are some tips to ensure your exam starts with a clean environment:
- You do not need external servers or resources.
- Do not register or connect to external repositories.
- Install a new VM according to the instructions in each practice exam.
- No sample solutions are provided for these practice exams. On the real exam, you need to be able to verify the solutions for yourself as well.
- You should be able to complete each exam within two hours.
- After applying these tips, you’re ready to get started. Good luck!
- Install a RHEL 9 virtual machine that meets the following requirements:
- 2 GB of RAM
- 20 GB of disk space using default partitioning
- One additional 20-GB disk that does not have any partitions installed
- Server with GUI installation pattern

#### Tasks
**<1>1**. Create user student with password password, and user root with password password.

**<1>2**. Configure your system to automatically mount the ISO of the installation disk on the directory /repo. Configure your system to remove this loop-mounted ISO as the only repository that is used for installation. Do not register your system with subscription-manager, and remove all references to external repositories that may already exist.

**<1>3**. Reboot your server. Assume that you don’t know the root password, and use the appropriate mode to enter a root shell that doesn’t require a password. Set the root password to mypassword.

**<1>4**. Set default values for new users. Set the default password validity to 90 days, and set the first UID that is used for new users to 2000.

**<1>5**. Create users edwin and santos and make them members of the group livingopensource as a secondary group membership. Also, create users serene and alex and make them members of the group operations as a secondary group. Ensure that user santos has UID 1234 and cannot start an interactive shell.

**<1>6**. Create shared group directories /groups/livingopensource and /groups/operations, and make sure the groups meet the following requirements:

<2>1. Members of the group livingopensource have full access to their directory.

<2>2. Members of the group operations have full access to their directory.

<2>3. New files that are created in the group directory are group owned by the group owner of the parent directory.

<2>4. Others have no access to the group directories.

**<1>7**. Create a 2-GiB volume group with the name myvg, using 8-MiB physical extents. In this volume group, create a 500-MiB logical volume with the name mydata, and mount it persistently on the directory /mydata.

**<1>8**. Find all files that are owned by user edwin and copy them to the directory/rootedwinfiles.

**<1>9**. Schedule a task that runs the command touch /etc/motd every day from Monday through Friday at 2 a.m.

**<1>10**. Add a new 10-GiB virtual disk to your virtual machine. On this disk, add a Stratis volume and mount it persistently.

**<1>11**. Create user bob and set this user’s shell so that this user can only change the password and cannot do anything else.

**<1>12**. Install the vsftpd service and ensure that it is started automatically at reboot.

**<1>13**. Create a container that runs an HTTP server. Ensure that it mounts the host directory /httproot on the directory /var/www/html.

**<1>14**. Configure this container such that it is automatically started on system boot as a system user service.

**<1>15**. Create a directory with the name /users and ensure it contains the subdirectories linda and anna. Export this directory by using an NFS server.

**<1>16**. Create users linda and anna and set their home directories to /home/users/linda and /home/users/anna. Make sure that while these users access their home directory, autofs is used to mount the NFS shares /users/linda and /users/anna from the same server.

--------------------
### RHCSA Practice Exam B

#### General Notes
- Here are some tips to ensure your exam starts with a clean environment:
- You do not need external servers or resources.
- Do not register or connect to external repositories.
- Install a new VM according to the instructions in each practice exam.
- No sample solutions are provided for these practice exams. On the real exam, you need to be able to verify the solutions for yourself as well.
- You should be able to complete each exam within two hours.
- After applying these tips, you’re ready to get started. Good luck!
- Install a RHEL 9 virtual machine that meets the following requirements:
- 2 GB of RAM
- 20 GB of disk space using default partitioning
- One additional 20-GB disk that does not have partitions installed
- Server with GUI installation pattern

#### Tasks
**<1>1**. Create user student with password password, and user root with password password.

**<1>2**. Configure your system to automatically mount the ISO of the installation disk on the directory /repo. Configure your system to remove this loop-mounted ISO as the only repository that is used for installation. Do not register your system with subscription-manager, and remove all references to external repositories that may already exist.

**<1>3**. Create a 1-GB partition on /dev/sdb. Format it with the vfat file system. Mount it persistently on the directory /mydata, using the label mylabel.

**<1>4**. Set default values for new users. Ensure that an empty file with the name NEWFILE is copied to the home directory of each new user that is created.

**<1>5**. Create users laura and linda and make them members of the group livingopensource as a secondary group membership. Also, create users lisa and lori and make them members of the group operations as a secondary group.

**<1>6**. Create shared group directories /groups/livingopensource and /groups/operations and make sure these groups meet the following requirements:

<2>1. Members of the group livingopensource have full access to their directory.

<2>2. Members of the group operations have full access to their directory.

<2>3. Users should be allowed to delete only their own files.

<2>4. Others should have no access to any of the directories.

**<1>7**. Create a 2-GiB swap partition and mount it persistently.

**<1>8**. Resize the LVM logical volume that contains the root file system and add 1 GiB. Perform all tasks necessary to do so.

**<1>9**. Find all files that are owned by user linda and copy them to the file /tmp/lindafiles/.

**<1>10**. Create user vicky with the custom UID 2008.

**<1>11**. Install a web server and ensure that it is started automatically.

**<1>12**. Configure a container that runs the docker.io/library/mysql:latest image and ensure it meets the following conditions

<2>1. It runs as a rootless container in the user linda account.

<2>2. It is configured to use the mysql root password password.

<2>3. It bind mounts the host directory /home/student/mysql to the container directory /var/lib/mysql.

<2>4. It automatically starts through a systemd job, where it is not needed for user linda to log in.

--------------------

### RHCSA Practice Exam C

#### General Notes
- Here are some tips to ensure your exam starts with a clean environment:
- You do not need any external servers or resources.
- Do not register or connect to any external repositories.
- Install a new VM according to the instructions in each practice exam.
- No sample solutions are provided for these practice exams. On the real exam, you need to be able to verify the solutions for yourself as well.
- You should be able to complete each exam within two hours.
- After applying these tips, you’re ready to get started. Good luck!
- Install a RHEL 9 virtual machine that meets the following requirements:
- 2 GB of RAM
- 20 GB of disk space using default partitioning
- One additional 20-GB disk that does not have any partitions installed
- Server with GUI installation pattern

#### Tasks
**<1>1**. Create user student with password password, and user root with password password.

**<1>2**. Configure your system to automatically mount the ISO of the installation disk on the directory /repo. Configure your system to remove this loop-mounted ISO as the only repository that is used for installation. Do not register your system with subscription-manager, and remove all references to external repositories that may already exist.

**<1>3**. Reboot your server. Assume that you don’t know the root password, and use the appropriate mode to enter a root shell that doesn’t require a password. Set the root password to mypassword.

**<1>4**. Set default values for new users. Make sure that any new user password has a length of at least six characters and must be used for at least three days before it can be reset.

**<1>5**. Create users linda and anna and make them members of the group sales as a secondary group membership. Also, create users serene and alex and make them members of the group account as a secondary group.

**<1>6**. Configure an SSH server that meets the following requirements:

<2>1. User root is allowed to connect through SSH.

<2>2. The server offers services on port 2022.

**<1>7**. Create shared group directories /groups/sales and /groups/account, and make sure these groups meet the following requirements:

<2>1. Members of the group sales have full access to their directory.

<2>2. Members of the group account have full access to their directory.

<2>3. Users have permissions to delete only their own files, but Alex is the general manager, so user alex has access to delete all users’ files.

**<1>8**. Create a 4-GiB volume group, using a physical extent size of 2 MiB. In this volume group, create a 1-GiB logical volume with the name myfiles, format it with the Ext3 file system, and mount it persistently on /myfiles.

**<1>9**. Create a group sysadmins. Make users linda and anna members of this group and ensure that all members of this group can run all administrative commands using sudo.

**<1>10**. Optimize your server with the appropriate profile that optimizes throughput.

**<1>11**. Add a new disk to your virtual machine with a size of 10 GiB. On this disk, create a LVM logical volume with a size of 5 GiB, configure it as swap, and mount it persistently.

**<1>12**. Create a directory /users/ and in this directory create the directories user1 through user5 using one command.

**<1>13**. Configure a web server to use the nondefault document root /webfiles. In this directory, create a file index.html that has the contents hello world and then test that it works.

**<1>14**. Configure your system to automatically start a mariadb container. This container should expose its services at port 3306 and use the directory /var/mariadb-container on the host for persistent storage of files it writes to the /var directory.

**<1>15**. Configure your system such that the container created in step 15 is automatically started as a Systemd user container.

--------------------


### RHCSA Practice Exam D

#### General Notes
- Here are some tips to ensure your exam starts with a clean environment:
- You do not need any external servers or resources.
- Do not register or connect to any external repositories.
- Install a new VM according to the instructions in each practice exam.
- No sample solutions are provided for these practice exams. On the real exam, you need to be able to verify the solutions for yourself as well.
- You should be able to complete each exam within two hours.
- After applying these tips, you’re ready to get started. Good luck!
- Install a RHEL 9 virtual machine that meets the following requirements:
- 2 GB of RAM
- 20 GB of disk space using default partitioning
- One additional 20-GB disk that does not have any partitions installed
- Server with GUI installation pattern

#### Tasks
**<1>1**. Create user student with password password, and user root with password password.

**<1>2**. Configure your system to automatically mount the ISO of the installation disk on the directory /repo. Configure your system to remove this loop-mounted ISO as the only repository that is used for installation. Do not register your system with subscription-manager, and remove all references to external repositories that may already exist.

**<1>3**. Create a 500-MiB partition on your second hard disk, and format it with the Ext4 file system. Mount it persistently on the directory /mydata, using the label mydata.

**<1>4**. Set default values for new users. A user should get a warning three days before expiration of the current password. Also, new passwords should have a maximum lifetime of 120 days.

**<1>5**. Create users lori and laura and make them members of the secondary group sales. Ensure that user lori uses UID 2000 and user laura uses UID 2001.

**<1>6**. Create shared group directories /groups/sales and /groups/data, and make sure the groups meet the following requirements:

<2>1. Members of the group sales have full access to their directory.

<2>2. Members of the group data have full access to their directory.

<2>3. Others has no access to any of the directories.

<2>4. Alex is general manager, so user alex has read access to all files in both directories and has permissions to delete all files that are created in both directories.

**<1>7**. Create a 1-GiB swap partition and mount it persistently.

**<1>8**. Find all files that have the SUID permission set, and write the result to the file /root/suidfiles.

**<1>9**. Create a 1-GiB LVM volume group. In this volume group, create a 512-MiB swap volume and mount it persistently.

**<1>10**. Add a 10-GiB disk to your virtual machine. On this disk, create a Stratis pool and volume. Use the name stratisvol for the volume, and mount it persistently on the directory /stratis.

**<1>11**. Install an HTTP web server and configure it to listen on port 8080.

**<1>12**. Create a configuration that allows user laura to run all administrative commands using sudo.

**<1>13**. Create a directory with the name /users and ensure it contains the subdirectories linda and anna. Export this directory by using an NFS server.

**<1>14**. Create users linda and anna and set their home directories to /home/users/linda and /home/users/anna. Make sure that while these users access their home directory, autofs is used to mount the NFS shares /users/linda and /users/anna from the same server.

--------------------
