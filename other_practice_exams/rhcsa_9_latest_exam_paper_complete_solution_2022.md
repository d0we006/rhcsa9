## RHCSA (EX 200) Examination Sample Question Paper Solutions


```
Max. Marks: 300
Time: 2.5 Hours (150 Minutes) Passing Score: 70% = 210/300


Note:
Ensure that all the tasks are implemented with firewalld and SELinux enabled. Your server should be able to survive the reboot.
```

### Questions

**1.** Configure the network:
Assign hostname and IP addresses for your virtual machines as per the following details:
Hostname - system1.eight.example.com
IP address 192.168.0.18 -
Netmask - 255.255.255.0
Gateway 192.168.0.1
Name Server - 8.8.8.8

#### **Solution to Task 1:**
```
#hostnamectl set-hostname system1.eight.example.com
#hostnamectl
#nmcli connection show
#ip a
# nmcli connection modify "System enp0s8" ipv4.addresses 192.168.0.18/24 ipv4.gateway
192.168.0.1 ipv4.dns 8.8.8.8 ipv4.method static
#nmcli connection up "System enp0s8"
#ping 192.168.0.1 #(To check ping with gateway)
```

**2.** Configure the repositories which are available on the repo server at:
http://repo.eight.example.com/BaseOS
http://repo.eight.example.com/AppStream

#### **Solution to Task 2:**
```
# dnf repolist all
#vim /etc/yum.repos.d/local.repo
[AppStream]
name=AppStream
baseurl=http://repo.eight.example.com/AppStream
enabled=1
gpgcheck=0

[BaseOS]
name=BaseOS
baseurl=http://repo.eight.example.com/BaseOS
enabled=1
gpgcheck=0
# dnf clean all
# dnf repolist all
# dnf install httpd -y
```

**3.** Configure the Selinux:
Your webcontent has been configured in port 85 at the /var/www/html directory (Don't alter or remove any files in this directory) make the content accessible.

#### **Solution to Task 3:**
```
#yum install httpd -y
# systemctl start httpd
# systemctl enable httpd
# cd /var/www/html
#echo Nehra Classes Are Awesome > file1
#cal > file2
#II
# semanage port -l | grep http #(check whether port 85 is enabled or if not use below command to add)
# dnf install -y policycoreutils*
# semanage port -l | grep http #(check whether port 85 is enabled or if not use below command to add)
#semanage port -a -t http_port_t-p tcp 85 #(-a-add, -t= type, -p=protocol)
#semanage port -l | grep http #(verify post 85 is added or not)
#firewall-cmd --permanent --add-port=85/tcp
#firewall-cmd --reload
#firewall-cmd --list-all #(check port 85 is added or not)

### Extra work
### Normally you will get error. If you want to get actual output in curl command
### Go to file /etc/httpd/conf/httpd.conf
### And goto line no 45
### Edit Listen value to 85 (Listen 85)
### Make sure your vm is pinging to google.com (#ping google.com)
# httpd -t #(it should show syntax ok)
# systemctl restart httpd
#curl http://192.168.0.18:85
#curl http://192.168.0.18:85/file1
#curl http://192.168.0.18:85/file2
```

**4.** Create the following users, groups and group memberships:
(a) A group named admin.
(b) A user harry who belongs to admin as a secondary group.
(c) A user natasha who belongs to admin as a secondary group.
(d) A user sarah who does not have access to an interactive shell on the system and who is not a member of admin.
(e) The users harry, natasha, sarah should all have password of password.

#### **Solution to Task 4:**
```
#groupadd admin
#useradd -G admin harry #(-G= secondary group, -g=primary group)
#useradd -G admin natasha
#useradd -s /sbin/nologin sarah #(-s=shell)
#passwd --stdin harry
#passwd --stdin natasha
#passwd --stdin sarah
Note: --stdin is not mandatory, if we use it no need to retype password and also it shows the password you typed.
#id harry; id natasha; id sarah
#tail/etc/group
#tail /etc/passwd
```

**5.** Create a collaborative directory /common/admin with the following characteristics:
(a) Group ownership of /common/admin is admin.
(b) The directory should be readable, writable and accessible to members of admin, but not any other user. (It is understood that root has access to all files and directories on the system.)
(c) Files created in /common/admin automatically have group ownership set to the admin group.

#### **Solution to Task 5:**
```
# mkdir -p /common/admin #(-p=parent directory)
#chgrp admin/common/admin
# chmod 770/common/admin
#Is -ld/common/admin
# chmod g+s/common/admin
# ls -ld/common/admin
#su - harry
```

**6.** Configure Autofs:
(a) to automatically mount the below NFS shares on system1.eight.example.com machine at /automount directory:
192.168.0.19:/public & 192.168.0.19:/private
(b) the public nfs share should have read only access for all users.
(c) the private nfs share should have read write access for all users.
(d) both shares should get automatically unmounted if not in use for 30 seconds

#### **Solution to Task 6: **
```
### Download packages:
dnf -y install autofs nfs-utils nfs4-acl-tools

### Create directories:
mkdir -p /automount/private 
mkdir -p /automount/public

### Edit /etc/auto.mmaster, and enter the following: 
/automount /etc/auto.automount --timeout=30

### Edit /etc/auto.automount, and enter the following:
public  -ro,sync        192.168.0.19:/public
private -rw,sync        192.168.0.19:/private

### restart autofs, and check: 
systemctl restart autofs
systemctl enable --now autofs
showmount -e
```

**7.** (a) Set a Cron job for harry on 12.30 at noon print "hello" using echo command.

#### **Solution to Task 7a:**
```
# crontab -eu harry
30 12 * * * /bin/echo "hello"
# crontab -lu harry #(it should show crontabs of that user) (-I-list, -u=user, -e=edit)

```

**7.** (b) Deny the natasha user to create a cronjob in system.
#### **Solution to Task 7b:**
```
#vim /etc/cron.deny
natasha
#su-natasha
# crontab -e
```

**8.** Configure ACL permissions:
Copy the file /etc/fstab to /var/tmp. Configure the permission of /var/tmp/fstab so that:
(a) The file /var/tmp/fstab is owned by root user.
(b) The file /var/tmp/fstab belongs to the group root.
(c) The file /var/tmp/fstab should not be executable by anyone.
(d) The user harry is able to read and write by /var/tmp/fstab.
(e) The user natasha can neither read nor write /var/tmp/fstab.
(f) All other users (current/future) have the ability to read /var/tmp/fstab

#### **Solution to Task 8:**
```
# cp/etc/fstab /var/tmp
# Is -l /var/tmp/fstab
# setfacl -m u:harry:rw /var/tmp/fstab
# setfacl -m u:natasha:---/var/tmp/fstab
# getfacl /var/tmp/fstab
```

**9.** Configure the NTP:
(a) Configure your system so that it is an NTP client of system2.eight.example.com (192.168.0.19)

#### **Solution to Task 9:**
```
# dnf install chrony* -y
#vim /etc/chrony.conf
server 192.168.0.19 iburst
#systemctl restart chronyd.service
#chronyc sources
```

**10.** Locate & copy the Files:
Find all files that greater than 4 MB in the /etc directory & copy them to /find/largefiles directory.

#### **Solution to Task 10:**
```
# mkdir -p /find/largefiles
#find /etc/-size +4M -type f-exec cp {}/find/largefiles/\;
# ls -lh/find/largefiles
```

**11.** (a) Create a new user with UID 1326, user name and password as alies.

#### **Solution to Task 11a:**
```
#useradd -u 1326 alies
#echo "alies" | passwd --stdin alies
#tail -1 /etc/passwd
```

**11.** (b) Create an archive file:
Backup the /var/tmp as /root/test.tar.gz

#### **Solution to Task 11b:**
```
#tar -zcvf/root/test.tar.gz /var/tmp #(-j for bzip2, -z for gzip)
# ls -l /root/
```

**11.** (c) Set the permissions:
(i) All new creating files for user natasha as 400 as default permission.
(ii) All new creating directories for user natasha as 500 as default permission

#### **Solution to Task 11c:**
```
#su - natasha
vim .bash_profile
umask 277
. .bash_profile
```

**12.** (a) The password for all new users in system1.eight.example.com should expires after 20 days.

#### **Solution to Task 12a:**
```
#vim /etc/login.defs
PASS_MAX_DAYS 20
#useradd new
#chage -l new
```

**12.** (b) Assign the sudo privilege:
Assign the Sudo Privilege for Group "admin" and Group members can administrate without any password.

#### **Solution to Task 12b:**
```
#vim /etc/sudoers
%admin ALL (ALL) NOPASSWD=ALL
```

**13.** Create a bash shell script program for:
(a) Create a mysearch script to locate file under /usr/share having size less than 1M.
(b) After executing the mysearch script file and listed (searched) files has to be copied under /root/myfiles.

#### **Solution to Task 13ab:**
```
# mkdir /root/myfiles
#vim mysearch
#!/bin/bash
find /usr/share -type f -size -1M -exec cp {}/root/myfiles\;
```

**14.** Reset the forgotten root password in system2.eight.example.com machine and set it as 'redhat'

**15.** (a) Create a swap partition 512MB size.

#### **Solution to Task 15a:**
```
# lsblk
#fdisk /dev/sdb
n (for new)
Press Enter (for primary)
Press Enter (for partition)
Press Enter (for starting size)
+512M (need to provide size as given in question)
t (type)
82 (for swap)
W (to save and exit)
#mkswap /dev/sdb1
### edit /etc/fstab and enter: 
UUID=#### swap swap defaults 0 0
### configure changes and check 
swapon -a 
swapon 
```

**15.** (b) Create one logical volume named database and it should be on datastore volume group with size 50 extent and assign the filesystem as ext3. the datastore volume group extend should be 8 MiB mount the logical volume under mount point /mnt/database.

**16.** Create the vectra volume using the VDO with the logical size 50 GB and mount under test directory.

**17.** Resize the logical volume size of +100 extents on /mnt/database directory.

#### **Solution to Task 17:**
```
# lvdisplay
#lvs
#lvextend -l 100 -r /dev/datastore/database
#lvs
```

**18.** Set the recommended tuned profile for your system.

#### **Solution to Task 18:**
```
#yum install tuned -y
# systemctl start tuned
# systemctl enable tuned
#tuned-adm profile
# tuned-adm recommend
# tuned-adm profile virtual-guest
# systemctl restart tuned
# tuned-adm active
```

**19.** Create the container as a system startup service.
(a) Create the container name as logserver with the images paradise user.
(b) The container should be configured as system startup services.
(c) The container directory is container_journal should be created on paradise user.

**20.** Configure the Container as persistent storage and create logs for container. 
(a) Configure the container with the persistent storage that mounted on /var/log/journal to /home/paradise/container.
(b) The container directory contains all journal files.

#### **Solution to Task 19-20 (missing a step/revisit later):**
```
### Create user paradise, and set password as password 
useradd paradise
passwd paradise

### Make journal persistent
mkdir /var/log/journal
systemctl restart systemd-journal-flush.service

### logged in as root: 
mkdir /var/log/journal
systemctl restart systemd-journal-flush.service
useradd paradise
passwd paradise 
loginctl enable-linger paradise 
loginctl show-user paradise 

### logged in as paradise user (fresh login => DO NOT USE 'su - paradise' => USE ssh paradise@ipaddress):
mkdir ~/container_journal
podman login
### Search container packages (e.g., NAME:docker.io/lendingworks/rsyslog Description:rsyslog containers):
podman search rsyslog
podman search rsyslog | less
podman run -d --name logserver -v /home/paradise/container_journal/:/var/log/journal:Z docker.io/corpusops/rsyslog
mkdir -p /home/paradise/.config/systemd/user
cd /home/paradise/.config/systemd/user/
podman generate systemd --name logserver --files --new
ls -Z
podman cat container-logserver.service
podman stop logserver
podman rm logserver

systemctl --user daemon-reload
echo $XDG_RUNTIME_DIR
id paradise
#export XDG_RUNTIME_DIR=/run/user/$( id -u)
systemctl --user enable container-logserver.service --now

### logged in as root: 
reboot

### logged in as user paradise (fresh login => DO NOT USE 'su - paradise' => USE ssh paradise@ipaddress)
### check to see if container started automatically 
podman ps 
```

#### Reference 
```
Title: # RHCSA 9 (EX 200) Latest Exam Paper Complete Solution 2022 | Redhat Exam Paper Solution & Information
Source: Youtube
Link: https://youtu.be/esbhLEM4zYc

Timestamps: 
0:41:03  Q6-Autofs
0:50:07  Q7-Cronjob
0:54:13  Q8-ACL
0:56:39  Q9-NTP
0:58:52  Q10-Locate&copy files
1:01:44  Q11-User, archive, permission 
1:08:48  Q12-Passwordexpiry,sudo privilege
1:11:57  Q13-Bash script 
1:14:38  Q14-Root password reset
1:25:44  Q15-Create swap partition, Logical volume
1:38:41  Q16-Create Vectra volume
```
