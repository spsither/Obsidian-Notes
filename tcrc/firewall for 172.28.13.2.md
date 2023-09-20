firewall rules are located in /etc/rc2.d/S46newfirewall

added bellow lines for ssh access to 172.28.13.2
$IPT -A INPUT -p tcp --dport 22 -m state --state NEW -s 172.28.21.107 -j ACCEPT
$IPT -A INPUT -p tcp --dport 22 -m state --state NEW -s 172.28.21.23 -j ACCEPT

added bellow lines for mysql connedtion
$IPT -A INPUT -p tcp --dport 3306 -m state --state NEW -s 172.28.21.107 -j ACCEPT
$IPT -A INPUT -p tcp --dport 3306 -m state --state NEW -s 172.28.21.23 -j ACCEPT

once changes are make do following to make changes take effect
> ./S46newfirewall