# Enable remote connection to MySQL database
Change the bind-address in mysql.cnf from 127.0.0.1 to * 
This allows remote machines that can access the server to connect to MySQL

> sudo vim /etc/mysql/mysql.conf.d/mysqld.cnf
or 
> sudo vim /etc/mysql/my.cnf

Set bind-address = * in the above file

> sudo systemctl restart mysql 
or
>sudo service mysql restart

If firewall is present allow access to 
> sudo ufw allow from 127.28.21.23 to any port 3306

for dot 2 do this [[firewall for 172.28.13.2]]

for dot 111 I did
>sudo iptables -A INPUT -p tcp --destination-port 3306 -j ACCEPT

In mysql 
> create user 'spsither'@'%' identified by 'blablabla';
> grant select on \*.\* to 'spsither'@'%';
> flush privileges;

to [[how to connect to MySQL on a specific port]]
