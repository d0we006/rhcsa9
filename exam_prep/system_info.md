## Sytem Info 

### Server 1
- Hostname: server1
- IPv4 Address: 192.168.0.18/24
- Gateway: 192.168.0.1
- DNS: 8.8.8.8
- IPv6 Address: fe80::a00:27ff:fe4d:56/64 

### Server 2
- Hostname: server2
- IPv4 Address: 192.168.0.19/24
- Gateway: 192.168.0.1
- DNS: 8.8.8.8
- IPv6 Address: fe80::a00:27ff:fe62:11c3/64
 
### Repo Information

-   [http://192.168.0.16/repo/BaseOS/](http://192.168.55.47/repo/BaseOS/)
-   [http://192.168.0.16/repo/AppStream/](http://192.168.55.47/repo/AppStream/)
-   [https://download-ib01.fedoraproject.org/pub/fedora/linux/releases/37/Everything/x86_64/os/](https://download-ib01.fedoraproject.org/pub/fedora/linux/releases/37/Everything/x86_64/os/)
-   Only use the Fedora Repo for packages unavailable on BaseOS or AppStream
-   The only thing on the task list that the Fedora repo is required for is to install "star" (Unique Standard Tape Archiver)
-   You can leave the Fedora repo disabled and only point to it for the one installation. If your repo ID is "F37", you would run the following command:
-   `dnf install -y star --repo F37`
