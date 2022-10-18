# Documentation of project 1
### In this project, i learnt about Web Stack Implementation used in AWS. I got to know that WEB STACkS are frameworks and tools to develop a particular software, applications, websites, etc. 
### In this project, i learnt and worked with LAMP (Linux, Apache, MySQl, PHP) WEB STACK.
### This project was done using the steps below:
#### 1. Setup AWS account and Provisioned an Ubuntu Server
### 2. Created an EC2 Instance and Connected to the EC2 Instance
- Got the SSH link of the Instance

![SSH link](./images\connect-instance1.PNG)

-Pasted the SSH link to  the terminal and connectted to the instance

![SSH connect](./images\ssh.PNG)
### 3. Installed Apache using Ubuntu’s package manager by running the code:
`sudo apt update`

`sudo apt install apache2`

`sudo systemctl status apache2`

### Verified that apache2 is running in the OS using the code:
`sudo systemctl status apache2`

![Apache status](./images\apache2-status.PNG)

### 4. I logged on into my new site using my IP address:
[My site](http://3.93.153.23:80)
![My site](./images\my-site.PNG)

### 5. Installed MySQL and logged into it by running the codes respectively:
`sudo apt install mysql-server`
![MySQL](./images\install-mysql.PNG)

`sudo mysql`
![MySQL login](./images\mysql_login.PNG)

### 6. Installed PHP using the code:
`sudo apt install php libapache2-mod-php php-mysql`
![PHP](./images\php-install.PNG)

### The version of the installed PHP was confirmed using the code:
`php -v`
![PHP version](./images\php-installed.PNG)

### 7. Apache Virtual Host: In order to test my PHP. i created a virtual host to hold the files of the new website that was created.
### - I created a domain name called **projectlamp** with the code:
`sudo mkdir /var/www/projectlamp`
### - And assigned an ownership to it as the user using:
`sudo chown -R $USER:$USER /var/www/projectlamp`
### - created a new configuration file in Apache’s sites-available directory 
`sudo vi /etc/apache2/sites-available/projectlamp.conf`
### - And pasted the test into the file as in the picture below:
![Apache configuration](./images\apache-config2.PNG)

### -  a2ensite command was run to enable the new virtual host:
`sudo a2ensite projectlamp`
### - The default website of  Apache was disabled using the a2dissite command :
`sudo a2dissite 000-default`
### - And in order ensure the configuration file doesn’t contain syntax errors, i run:
`sudo apache2ctl configtest`
### - Finally reloaded Apache so these changes take effect using the code:
`sudo systemctl reload apache2`
### - Created an index.html file to test the virtual host functionality using the code:

`sudo echo 'Hello LAMP from hostname' $(curl -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(curl -s http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectlamp/index.html`
### The effact as shown below revealed the website was updated:
![Site update](./images\new-site1.PNG)

### 7. Enabled PHP on the website
### - At first, i gave the *index.php* precedence over the *index.html* by changing the order of display in the **/etc/apache2/mods-enabled/dir.conf** file using the code :
`sudo vim /etc/apache2/mods-enabled/dir.conf`

from this:
![Site update](./images\change-order2.PNG)
to this:
![Site update](./images\change-order3.PNG)

### - The apache was reloaded using thw code:
`sudo systemctl reload apache2`
### - I created a new file named *index.php* inside the custom web root folder using the code:
`vim /var/www/projectlamp/index.php`
### - And added the following PHP code inside the file as shown below: 
![Site update](./images\php-site1.PNG)
 ### The information page about the server was duisplayed from the perspective of PHP as shown below:
 ![Site update](./images\php-site2.PNG)
 ### The picture above is an indication that PHP was installed successfully and functional as well.
 ### The next line of action was the removal of the *php* file created so that i do not reveal to the public sensitive information about my PHP environment -and my Ubuntu server. This was done using the following code:
`sudo rm /var/www/projectlamp/index.php`

### This PBL project has really helped in making me to understand WEB STACKs and their usefulness in modern day software production. 