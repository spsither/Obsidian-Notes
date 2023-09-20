
[ref](https://www.digitalocean.com/community/tutorials/how-to-use-apache-as-a-reverse-proxy-with-mod_proxy-on-ubuntu-16-04)

A _reverse proxy_ is a type of proxy server that takes HTTP(S) requests and transparently distributes them to one or more backend servers. Reverse proxies are useful because many modern web applications process incoming HTTP requests using backend application servers. These servers aren’t meant to be accessed by users directly, and often only support rudimentary HTTP features.

You can use a reverse proxy to prevent these underlying application servers from being directly accessed. They can also be used to distribute the load from incoming requests to several different application servers, increasing performance at scale and providing fail-safeness. They can fill in the gaps with features the application servers don’t offer, such as caching, compression, or SSL encryption.

`sudo a2enmod proxy`
`sudo a2enmod proxy_http`
`sudo a2enmod proxy_balancer`
`sudo a2enmod lbmethod_byrequests`

`sudo a2enmod rewrite`

`sudo systemctl restart apache2`


## Virtual host config for museum Next.js app
```xml
<VirtualHost *:80>
    ServerAdmin spsither@gmail.com
    ServerName interactive.tibetmuseum.org
    ServerAlias www.interactive.tibetmuseum.org
    DocumentRoot /var/www/interactive.tibetmuseum.org/react-tibet-museum
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
    ProxyRequests on
    ProxyPass / http://localhost:3000/
    ProxyPassReverse / http://localhost:3000/
    RewriteEngine on
    RewriteCond %{SERVER_NAME} =interactive.tibetmuseum.org [OR]
    RewriteCond %{SERVER_NAME} =www.interactive.tibetmuseum.org
    RewriteRule ^ https://%{SERVER_NAME}%{REQUEST_URI} [END,NE,R=permanent]
</VirtualHost>
<VirtualHost *:443>
    ServerAdmin spsither@gmail.com
    ServerName interactive.tibetmuseum.org
    ServerAlias www.interactive.tibetmuseum.org
    DocumentRoot /var/www/interactive.tibetmuseum.org/react-tibet-museum
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
    ProxyRequests on
    ProxyPass / http://localhost:3000/
    ProxyPassReverse / http://localhost:3000/
    SSLEngine on
    SSLCertificateFile /etc/cloudflare/interactive.tibetmuseum.org.pem
    SSLCertificateKeyFile /etc/cloudflare/interactive.tibetmuseum.org.key
</VirtualHost>
```