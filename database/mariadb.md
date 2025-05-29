# First open terminal and then type

~ sudo pacman -S mariadb

# Second Command type...

~ sudo mysql_install_db --user=mysql --basedir=/usr --datadir=/var/lib/mysql

# Third Comand.....
 
 ~ sudo systemctl enable mariadb.service
 
# Fourth Command....
 
 ~ sudo systemctl start mariadb.service
 
 
# After that close your terminal and again open
 
# Type follwing command....
 
 
 ~ sudo mysql_secure_installation
 
# then type your root password then set new password then again retype it press enter
 
 
 Now You are ask to proceed some question just doing what I select
 
 Remove Anonymous users? [Y/N] y
 
 Disallow root login remotely?  [Y/N] y
 
 
 Remove test database and access to it?  [Y/N] y
 
 
 Reload privilege tables now?  [Y/N] y
 
 
 
# Now that's all right.....
 
 
 restart/reboot your system/pc
 
# Move on.....
 
# open terminal again.....
 
 
# type as I type what...
 
 ~ sudo mysql -u root -p
 
# type your system pass then type [NB:Do not miss to type semicolon(;)]
 
 CREATE USER 'username'@'localhost' IDENTIFIED BY 'password';
 
 On 'username' --- "write your username"
 
 On 'some_pass' --- "write your password"
 
# then press enter then type following put your selected username properly  at 'username'
 
 
  GRANT ALL PRIVILEGES ON *.* TO 'username'@'localhost';
  
  flush privileges;
  
  quit

