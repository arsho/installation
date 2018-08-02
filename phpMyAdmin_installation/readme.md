Install PHPMyadmin in Ubuntu 16.04
=========================================

### Environment

* <b> Operating System</b> : Ubuntu 16.04 LTS (64-bit)
* <b> MySQL</b> : Ver 14.14 Distrib 5.7.21, for Linux (x86_64) using  EditLine wrapper
#### Install Apache2
```
sudo apt-get -y install apache2
```
#### Install PHP
```
sudo apt-get -y install php7.0 libapache2-mod-php7.0
sudo apt-get install php-mbstring php7.0-mbstring php-gettext
systemctl restart apache2
php --version
```
#### Install phpMyAdmin
```
sudo apt-get -y install phpmyadmin
sudo systemctl restart mysql.service
```
#### Edit Apache webserver config file
```
sudo nano /etc/apache2/apache2.conf
```
Add the following line at the end:
```
Include /etc/phpmyadmin/apache.conf
```
Restart Apache server
```
sudo systemctl restart apache2
```
#### Access PHPMyadmin
Go to ```http://localhost/phpmyadmin/```

#### Add File read/write permission for current user in `/var/www` directory:
```
➜  ~ whoami
arsho
➜  ~ sudo adduser arsho www-data
[sudo] password for arsho: 
Adding user `arsho' to group `www-data' ...
Adding user arsho to group www-data
Done.
➜  ~ sudo chown -R www-data:www-data /var/www
➜  ~ sudo chmod -R g+rwX /var/www
```
Logout and Login again.

#### References

* Install phpMyAdmin with LAMP stack on Ubuntu 16.04: [https://www.ostechnix.com/install-phpmyadmin-with-lamp-stack-on-ubuntu-16-04/](https://www.ostechnix.com/install-phpmyadmin-with-lamp-stack-on-ubuntu-16-04/)
* Whats the simplest way to edit and add files to “/var/www”: [https://askubuntu.com/a/51337/654735](https://askubuntu.com/a/51337/654735)

