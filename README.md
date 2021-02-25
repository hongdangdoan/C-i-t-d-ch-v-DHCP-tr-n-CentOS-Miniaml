# C-i-t-d-ch-v-DHCP-tr-n-CentOS-Miniaml
Install dhcp
yum install -y dhcp
Write config:
vi /etc/dhcp/dhcpd.conf
Information about ip address allocation:
cat /var/lib/dhcpd/dhcpd.leases
Check config file:
dhcpd
Config firewall:
iptables -A INPUT -p udp -m state --state NEW --dport 67 -j ACCEPT
firewall-cmd --add-service=dhcp --permanent
firewall-cmd --reload 
Start dhcpd services:
systemctl start dhcpd
Check status of dhcpd services:
dhcpd
Check if there is a DHCPd service is listening socket port 67 udp:
netstat -ulnp | grep 67
Check if there is a DHCPD service running
ps -aux | grep dhcpd
Allow dhcpd start with system:
systemctl enable dhcpd
