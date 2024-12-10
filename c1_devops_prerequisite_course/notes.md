## Linux Commands

| Command | Purpose |
| ------- | ------- |
| wget <url_of_file> -O <filename.ext> | Download a file and save as filename |
| cat /etc/*release* | To see the release version of linux OS |
| rpm -i <package_name.rpm> | CentOS : Install a package |
| rpm -e <package_name.rpm> | CentOS : Uninstall a package |
| rpm -q <package_name.rpm> | CentOS : Query a package |
| yum install <package_name> | CentOS : Where rpm does not work, yum comes to rescue |
| yum remove <package_name> | CentOS : Uninstall the package earlier installed by yum |
| yum repolist | CentOS : list of yum installed packages |
| whoami  | user name |
| id | id of user and the group id |
| su <new_user> | to switch user |
| ssh <user_name>@<IP> | to connect remotely |
| ls /root | only root user can open this |
| sudo ls /root | regular user can do sudo jobs |
| curl <url> -O | download file |
| service <service_name> start | start the service like dockers |
| systemctl start <service_name> | same purpose as above |
| systemctl stop <service_name> | stop the service |
| systemctl status <service_name> | check the status of service whether it is activated or not |
| systemctl enable <service_name> | configure service to start at startup |
| systemctl disable <service_name> | configure service to NOT start at startup |
| ip link | to see the networking interface e.g. eth0 |
| ip addr add <ip_address> dev eth0 | to assigne an ip on the network |
| ping <another_ip_address> | to check whether communicating with another computer on the same network |
| route | to see the status of permissions through gateway |
| ip route add <ip_address_from_another_network> via <ip_address_of_the_router> | to add an ip from another network to communicate |
| ip route add default via <ip_of_router> | to connect with the internet. default can replaced by 0.0.0.0 |
| cat /etc/hosts | to check the hosts. nano to modify it |
| cat /etc/resolv.conf | to declare/add/ check the ip of dns server |
| nslookup <domain_name> | gives details of the domain name |

- To make a system-defined service treated by systemctl, 
    - first you have to navigate to `/etc/systemd/system` folder.
    - then make a file ``<service_name>.service``
    - in this file write the following code. e.g. for python
        ```
        # Description of the service
        [Unit]
        Description=My python web application

        # The service to run
        [Service]
        # the service to start
        ExecStart=/usr/bin/python3 /opt/code/my_app.py
        # the service to start before (not mandatory)
        ExecStartPre=/opt/code/configure_db.sh
        # the service to start after (not mandatory)
        ExecStartPost=/opt/code/email_status.sh
        # to restart if crashes
        Restart=always

        # On startup, the service should run after multi-user.target
        [Install]
        WantedBy=multi-user.target
        ```
    - then run `systemctl daemon-reload`
    - then run `systemctl start <service_name>`
    - et voila!
- A switch manages the traffic within a network (i.e. an intra-network communication)
- A router manages the traffic between multiple networks (i.e. an inter-network communication)
- a gateway allows the traffic from one network to another
- DNS server has all the host ip-addresses and names to check with. It is a server in the network which keeps record of all the internal as well external ip addresses and their names.
- `nameserver 8.8.8.8` is a DNS host file, maintained by google for publicly accessible hosts.
- 