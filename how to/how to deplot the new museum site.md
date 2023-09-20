[[how to install LAMP stack on ubuntu]]

[How to Configure CloudFlare Origin CA for Apache](https://devanswers.co/configure-cloudflare-origin-ca-apache/)

api.tibetmuseum.org.conf
```xml
<VirtualHost *:80>

ServerName api.tibetmuseum.org

ServerAlias www.api.tibetmuseum.org

  

ServerAdmin webmaster@localhost

DocumentRoot /var/www/api.tibetmuseum.org/museum-backend/public

<Directory "/var/www/api.tibetmuseum.org/museum-backend">

    Options +FollowSymLinks

            RewriteEngine On

            AllowOverride All

            Require all granted

</Directory>

ErrorLog ${APACHE_LOG_DIR}/error.log

CustomLog ${APACHE_LOG_DIR}/access.log combined

  

RewriteEngine on

RewriteCond %{SERVER_NAME} =api.tibetmuseum.org [OR]

RewriteCond %{SERVER_NAME} =www.api.tibetmuseum.org

RewriteRule ^ https://%{SERVER_NAME}%{REQUEST_URI} [END,NE,R=permanent]

</VirtualHost>

  

<VirtualHost *:443>

        ServerName api.tibetmuseum.org

        ServerAlias www.api.tibetmuseum.org

  

        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/api.tibetmuseum.org/museum-backend/public

        <Directory "/var/www/api.tibetmuseum.org/museum-backend">

            Options +FollowSymLinks

            RewriteEngine On

            AllowOverride All

            Require all granted

        </Directory>

  

        ErrorLog ${APACHE_LOG_DIR}/error.log

        CustomLog ${APACHE_LOG_DIR}/access.log combined

SSLEngine on

SSLCertificateFile /etc/cloudflare/api.tibetmuseum.org.pem

SSLCertificateKeyFile /etc/cloudflare/api.tibetmuseum.org.key

  

</VirtualHost>

```

interactive.tibetmuseum.org.conf
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


Note that for NextJs I am using  [[how to Apache reverse proxy]] and [[how to tmux]] to keep the node app running.

For MySQL I did [[how to secure MySQL installation]]

I had to add the following line in `_app.js`  to avoid `UNABLE_TO_VERIFY_LEAF_SIGNATURE` certificate verification error when react tries to hit api in the same virtual machine.
```javascript
process.env.NODE_TLS_REJECT_UNAUTHORIZED = "0";
```

This has to be removed because the proper solution should be to put the self-signed certificate in your trusted root store OR to get a proper certificate signed by an existing Certificate Authority (which is already trusted by your server).


# Whitelist museum server on CloudFlare 
 navigating to the Security → WAF → Tools → IP Access Rules → allow