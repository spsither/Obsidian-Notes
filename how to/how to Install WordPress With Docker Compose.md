****
[DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-with-docker-compose#step-5-modifying-the-web-server-configuration-and-service-definition)

## Initial setup
>adduser sammy
>usermod -aG sudo sammy
>ufw app list
>ufw allow OpenSSH
>ufw allow http
>ufw allow https
>ufw enable
>ufw status

## Install Docker 
>sudo apt update
>sudo apt install apt-transport-https ca-certificates curl software-properties-common
>curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
>sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
>apt-cache policy docker-ce
>sudo apt install docker-ce
>sudo systemctl status docker
>sudo usermod -aG docker ${USER}
>su - ${USER}
[[Musueum migration]]

## Install Docker Compose
>sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
>sudo chmod +x /usr/local/bin/docker-compose
>docker-compose --version

## Defining the Web Server Configuration
>mkdir wordpress
>cd wordpress
>mkdir nginx-conf
>nano nginx-conf/nginx.conf
```json
server {
        listen 80;
        listen [::]:80;

        server_name your_domain www.your_domain;

        index index.php index.html index.htm;

        root /var/www/html;

        location ~ /.well-known/acme-challenge {
                allow all;
                root /var/www/html;
        }

        location / {
                try_files $uri $uri/ /index.php$is_args$args;
        }

        location ~ \.php$ {
                try_files $uri =404;
                fastcgi_split_path_info ^(.+\.php)(/.+)$;
                fastcgi_pass wordpress:9000;
                fastcgi_index index.php;
                include fastcgi_params;
                fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
                fastcgi_param PATH_INFO $fastcgi_path_info;
        }

        location ~ /\.ht {
                deny all;
        }
        
        location = /favicon.ico { 
                log_not_found off; access_log off; 
        }
        location = /robots.txt { 
                log_not_found off; access_log off; allow all; 
        }
        location ~* \.(css|gif|ico|jpeg|jpg|js|png)$ {
                expires max;
                log_not_found off;
        }
}
```

## Defining Environment Variables
>nano .env
```
MYSQL_ROOT_PASSWORD=your_root_password
MYSQL_USER=your_wordpress_database_user
MYSQL_PASSWORD=your_wordpress_database_password
```

## Defining Services with Docker Compose
>nano docker-compose.yml

```yml
version: '3'

  

services:

db:

image: mysql:8.0

container_name: db

restart: unless-stopped

env_file: .env

environment:

- MYSQL_DATABASE=wordpress

volumes:

- dbdata:/var/lib/mysql

command: '--default-authentication-plugin=mysql_native_password'

networks:

- app-network

  

wordpress:

depends_on:

- db

image: wordpress:5.1.1-fpm-alpine

container_name: wordpress

restart: unless-stopped

env_file: .env

environment:

- WORDPRESS_DB_HOST=db:3306

- WORDPRESS_DB_USER=$MYSQL_USER

- WORDPRESS_DB_PASSWORD=$MYSQL_PASSWORD

- WORDPRESS_DB_NAME=wordpress

volumes:

- wordpress:/var/www/html

networks:

- app-network

  

webserver:

depends_on:

- wordpress

image: nginx:1.15.12-alpine

container_name: webserver

restart: unless-stopped

ports:

- "80:80"

volumes:

- wordpress:/var/www/html

- ./nginx-conf:/etc/nginx/conf.d

networks:

- app-network

volumes:

wordpress:

dbdata:

  

networks:

app-network:

driver: bridge
```

## Start your containers
>docker-compose up -d
>docker-compose ps


**.**

├── docker-compose.yml
├── **nginx-conf**
 │         └── nginx.conf
└── php.ini
└── .htaccess

### .htaccess
```
# BEGIN WordPress

<IfModule mod_rewrite.c>

RewriteEngine On

RewriteBase /

RewriteRule ^index\.php$ - [L]

RewriteCond %{REQUEST_FILENAME} !-f

RewriteCond %{REQUEST_FILENAME} !-d

RewriteRule . /index.php [L]

</IfModule>

  

php_value upload_max_filesize 2048M

php_value post_max_size 2048M

php_value memory_limit 256M

php_value max_execution_time 3600

php_value max_input_time 3600

  

# END WordPress
```

### php.ini


To import a sql file in MySQL running on Docker
>docker exec -i mysql_container mysql -uroot -psecret mysql < db.sql
