## Install PHP, MySQL, phpMyAdmin in Ubuntu 18.04 LTS
### Install Mysql Server and MySQL Client
#### What is the difference between MySQL Server and MySQL Client?
<b>MySql Client:</b>
The `mysql-client` package allows you to connect to a MySQL server. It will give you the `mysql` command-line program.

<b>MySql Server:</b>
The `mysql-server` package allows to run a MySQL server which can host multiple databases and process queries on those databases.

- Update Ubuntu
  ```
  sudo apt update
  ```

- Upgrade Ubuntu
  ```
  sudo apt upgrade
  ```

- Install MySQL Server
  ```
  sudo apt install mysql-server
  ```
  Enter root user password if asked.

- Install MySQL Client
  ```
  sudo apt install mysql-client
  ```

- Configure MySQL
  ```
  sudo mysql_secure_installation
  [sudo] password for USER_NAME_OF_MACHINE: 
  Would you like to setup VALIDATE PASSWORD plugin?
  Press y|Y for Yes, any other key for No: 

  Please set the password for root here.
  New password: 
  Re-enter new password: 

  Remove anonymous users? (Press y|Y for Yes, any other key for No) : y
  Success.

  Disallow root login remotely? (Press y|Y for Yes, any other key for No) : 
  ... skipping.
  
  Remove test database and access to it? (Press y|Y for Yes, any other key for No) :   
  ... skipping.

  Reload privilege tables now? (Press y|Y for Yes, any other key for No) : y
  Success.

  All done!  
  ```

- Test MySQL service
  ```
  systemctl status mysql.service
  ```

- Test connecting to database
  ```
  sudo mysqladmin -p -u root version
  ```

- Open Mysql Console
  ```
  sudo mysql -p -u root
  ```

- In case the MySQL is not running, start it with
  ```
  sudo systemctl start mysql
  ```

- In case you need to restart MySQL, restart it with
  ```
  sudo systemctl restart mysql
  ```

- Create database in MySQL console
  ```
  create database cp_intrafish;
  ```

- Install `mysql-config`
  ```
  sudo apt-get install libmysqlclient-dev
  ```

- Load Database dump to the newly created database. Here `cp_intrafish` is the database name and `myifm_dump.sql` is the SQL dump file.
  ```
  mysql -p -u root cp_intrafish<myifm_dump.sql
  ```

- Pretty output in MySQL console. Add `\G` at the end of your command. This will change the output just for that command, without changing the default output. 
  ```
  SELECT * FROM product_price\G;
  ```
### Install Apache2
  ```
  sudo apt-get -y install apache2
  ```
### Install PHP
  ```
  sudo apt-get -y install php libapache2-mod-php
  sudo apt-get -y install php-mbstring php-mbstring php-gettext
  systemctl restart apache2
  php --version
  ```
### Install phpMyAdmin
  ```
  sudo apt-get -y install phpmyadmin
  sudo systemctl restart mysql.service
  ```
### Edit Apache webserver config file
  ```
  sudo nano /etc/apache2/apache2.conf
  ```
- Add the following line at the end:
  ```
  Include /etc/phpmyadmin/apache.conf
  ```
- Restart Apache server
  ```
  sudo systemctl restart apache2
  ```
- To access phpMyAdmin go to ```http://localhost/phpmyadmin/```
#### Handling Error in accessing database using phpMyAdmin
MySQL 5.7 changed the secure model: now MySQL root login requires a sudo.

I.e., phpMyAdmin will be not able to use root credentials.

The simplest, safest and permanent solution will be create a new user and grant required privileges.

- Connect to MySQL
  ```
  sudo mysql --user=root mysql
  ```
- Create an user for phpMyAdmin
  Replace `some_pass` by the desired password:
  ```
  CREATE USER 'phpmyadmin'@'localhost' IDENTIFIED BY 'some_pass';
  ```
  If you get `ERROR 1396 (HY000): Operation CREATE USER failed for 'phpmyadmin'@'localhost'`, check if you have already an user called `phpmyadmin` using:
  ```
  select user,host from user;
  ```
  Then give all privileges to the user:
  ```
  GRANT ALL PRIVILEGES ON *.* TO 'phpmyadmin'@'localhost' WITH GRANT OPTION;
  FLUSH PRIVILEGES;
  ```

### Add File read/write permission for current user in `/var/www` directory:
  ```
  ➜  ~ whoami
  YOUR_USER_NAME
  ➜  ~ sudo adduser arsho www-data
  [sudo] password for YOUR_USER_NAME: 
  Adding user `YOUR_USER_NAME' to group `www-data' ...
  ➜  ~ sudo chown -R www-data:www-data /var/www
  ➜  ~ sudo chmod -R g+rwX /var/www
  ```
 - Logout and Login again.



### Reference:
- [Stackoverflow answer on phpMyAdmin login error](https://askubuntu.com/a/763359/654735)
