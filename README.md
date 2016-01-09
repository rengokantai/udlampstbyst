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

3-4
edit php.ini  (in /etc folder)
```
short_optn_tag =on
```

3-5
install google pagespeed
```
yum install at
rpm -Uvh ...pagespeed.rpm
/etc/init.d/httpd restart
```

3-6
php-gd (image thumbnails)
```
yum install php-gd
/etc/init.d/httpd restart
```



3-7
setting permissions to upload dict
```
chgrp apache /var/www/html/upload(images)
chmod 777 /var/www/html/upload(images)
chown apache /var/www/html/upload(images)
sudo /etc/init.d/httpd restart
```
3-8
```
yum install mod_ssl
chown ec2-user /etc/httpd/conf.d
chown ec2-user /etc/pki/tls/certs
```
edit ssl.conf
```
```
4-1
Go to godaddy, select domain, Add new ->
Record type : A
host:@
Point to: elastic ip

6-1
modify .htaccess to enable multiple host access
```
<ifModule mod_gzip.c>
mod_gzip_on Yes
mod_gzip_dechunk Yes
mod_gzip_item_include_file .(html?|txt|css|js|php)$
mod_gzip_item_include mime ^text/.*
mod_gzip_item_exclude rspheader ^Content-Encoding:.*gzip.*
</ifModule>


