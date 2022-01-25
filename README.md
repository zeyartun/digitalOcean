# digitalOcean

https://github.com/thetminnhtun/web-development-note/blob/master/hosting_laravel_on_digitalocean.md
https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys-2

Digital ocean install php for Apache => https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-20-04#step-4-%E2%80%94-creating-a-virtual-host-for-your-website

ssl => https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-ubuntu-20-04
https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-ubuntu-16-04
ssl => https://certbot.eff.org/lets-encrypt/ubuntufocal-nginx

database root access => https://tableplus.com/blog/2018/10/how-to-create-a-superuser-in-mysql.html

# composer Update 1 to 2
https://www.digitalocean.com/community/tutorials/how-to-install-composer-on-ubuntu-20-04-quickstart

server => https://laravel.com/docs/8.x/deployment

apt update
apt upgrade
apt install nginx -y
http://server_domain_or_IP
cd /var/www/html/index.nginx-debian.html

PHP
apt install php-fpm php-mysql

For Laravel and composer

apt install php php-curl php-common php-cli php-mysql php-mbstring php-fpm php-bcmath php-xml php-zip -y

MySQL
apt install mysql-server -y
mysql_secure_installation
mysql -u root
SELECT user,authentication_string,plugin,host FROM mysql.user;

ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'your_password';
FLUSH PRIVILEGES;
mysql -u root -p
nano /etc/nginx/sites-available/default
#############################################################################
server { 

listen 80; 

    server_name api.asxox.com.mm www.api.asxox.com.mm; 

    root /var/www/asxox-api/public; 

    index index.html index.htm index.php; 

    location / { 

        try_files $uri $uri/ /index.php?$args; 

    } 

    location ~ \.php$ { 

        include snippets/fastcgi-php.conf; 

        fastcgi_pass unix:/var/run/php/php7.4-fpm.sock; 

     } 


    location ~ /\.ht { 

        deny all; 

    } 

} 
#################################################
nginx -t

systemctl reload nginx
