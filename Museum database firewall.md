[iptables](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-using-iptables-on-ubuntu-12-04)

issue is with mysql. Should be OFF.
 >SHOW VARIABLES LIKE 'skip_networking';
 ON


--skip-networking option is given when mysql started
>ps ax | grep mysql
>25400 ?        S      0:00 /bin/sh /usr/bin/**mysql**d_safe --skip-grant-tables --skip-networking


1. check if port is listened to
	`sudo netstat -ntlup`
2. verify also that the bind-address is set to *
3. check the firewall rule
	`sudo iptables -L -n`

```
sudo iptables -I INPUT -p tcp -m tcp --dport 80 -j ACCEPT
```

```
sudo service iptables save
```
