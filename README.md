#### udlampstbyst
3-1 install php
```
yum install php-mysql php php-xml php-mcrypt php-mbstring php-cli php-soap mysql httpd
```
start httpd:
```
/etc/init.d/httpd restart
```

3-2
```
yum install mysql-server
```
```
/etc/init.d/mysqld restart
```
```
mysqladmin -u root password 'pass'
```
```
CREATE USER 'user'@'localhost' IDENTIFIED BY 'pass'
```
```
wget phpmyadmin
```
copy the unzipped folder to /var/www/html:
```
tar -zxvf phpadmin -C /var/www/html
```
3-3
```
sudo chown ec2-user /etc/httpd/conf
```
open httpd.conf
```
AllowOverride None->All
```
Then,restart httpd
```
/etc/init.d/httpd restart
```
Rewrite .htaccesscopy to html folder
```
ReWriteEngine On
RewriteRule ^([^.]+)/?$  /index.php?name=$1 [L,QSA]
```


