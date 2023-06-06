# Adobe_Coldfusion_Installation

### To install Coldfusion in Ubuntu first go to this site.

[https://helpx.adobe.com/coldfusion/kb/coldfusion-downloads.html](https://helpx.adobe.com/coldfusion/kb/coldfusion-downloads.html)

### image1
	
![alt text](https://github.com/faheemmalik11/Adobe_Coldfusion_Installation/blob/development/ss1.png?raw=true)



From options select 
```sh 
Adobe ColdFusion (2021 release)
```
And then click on the blue download button 

Then logged In into the user (using google or create a new account).

Then download the new package by filling the form at the last of the form select 
```sh
linux - GUI | English | 1.57GB
```
### image2

![alt text](https://github.com/faheemmalik11/Adobe_Coldfusion_Installation/blob/development/ss2.png?raw=true)

The download will start shortly.


Then go to downloaded directory then open terminal then change the permission using this command :

```sh
chmod +x ColdFusion_2023_GUI_WWEJ_linux64.bin
```

Then the dialog box will open.

### image3
![alt text](https://github.com/faheemmalik11/Adobe_Coldfusion_Installation/blob/development/ss3.png?raw=true)

select 30-day trial option


### image4
OR

### image5


### image6

### image7

### image8

### image9
Password : Adobe@11

(* Don’t change the username and remember the given admin username and password)

### image10
Don’t make any changes


After complete installation then go to this folder :
```sh
/opt/ColdFusion2023/cfusion/bin
```

Then open terminal to Start Server

```sh
sudo ./coldfusion start
```

Check for server response by this path:

[http://127.0.0.1:8500/CFIDE/administrator/index.cfm](http://127.0.0.1:8500/CFIDE/administrator/index.cfm)

If link is not working then please remove index.cfm from the link

And enter the login credentials that you have given during setup.
And this screen will appear: 
### image11


To add new file in wwwroot give permission to the root(wwwroot)
Open path:
```sh
/opt/ColdFusion2023/cfusion
```
command:
```sh
sudo chmod 777 wwwroot/
```

#MySql & MsSql Setup Document 
##MySQL Setup

[https://www.digitalocean.com/community/tutorials/how-to-install-mysql-on-ubuntu-20-04](https://www.digitalocean.com/community/tutorials/how-to-install-mysql-on-ubuntu-20-04)

Step 1: Open up the terminal and execute the following command:
```sh
sudo apt update
```
Step 2: Supply your password and wait for the update to finish. Next, run the following command:
```sh
y
```

Step 3: Run the following command to install MySQL Server:
```sh
sudo apt install mysql-server
```

A Popup show for password (passowrd:Adobe@11)
### image12

Step 4: Ensure that the server is running using the systemctl start command:

```sh
sudo systemctl start mysql.service
```

Step 5: Configuring MySQL:
Then run this command in terminal :
```sh
Mysql_secure_installation
```
Password validation policy : your choice
[ 	 LOW    Length >= 8
MEDIUM Length >= 8, numeric, mixed case, and special characters
STRONG Length >= 8, numeric, mixed case, special characters and dictionary   	]


### image13

(there is a error, while running in this command)
For this error: 
Follow these steps:
First, open up the new terminal then open MySQL prompt:
```sh
sudo mysql
```
Then run the following ALTER USER command to change the root user’s authentication method to one that uses a password. 
```sh
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
```
After making this change, exit the MySQL prompt:
```sh
exit
```


Run the security script

(remember the password that you have given will installation).
Then the mysql will install and return a success message.
### image14



If there is a issue with this open cli for mysql
### image15

Then error will be:ERROR 1698 (28000): Access denied for user 'root'@'localhost'
Then run these commands.
```sh
sudo mysql -u root
```

```sh
USE mysql
```

```sh
UPDATE user SET plugin='mysql_native_password' WHERE User='root'
```

```sh
FLUSH PRIVILEGES 
```

```sh
exit
```

```sh
sudo service mysql restart
```

If there is a issue like.ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
### image16

Then run this command :
```sh
sudo mysql -u root -p
```
### image17

Then install Workbench from the store For GUI interface .
Then Edit connection.


### image18

First in the password Store in keychain enter your root user password .
If there is a error like :

### image19

Then run this command :
You need to enter a command to allow this package to access the service. The command is:
```sh
sudo snap connect mysql-workbench-community:password-manager-service :password-manager-service
```

Then press the test Connection button in footer

There will be a success massage:


### image20

### Mysql Workbench

[https://linuxhint.com/installing_mysql_workbench_ubuntu/](https://linuxhint.com/installing_mysql_workbench_ubuntu/)


To install mysql Workbench:

```sh
sudo snap install mysql-workbench-community
```

### MsSQL Setup

By using official documentation of microsoft to install Mssql.


[https://docs.microsoft.com/en-us/sql/linux/quickstart-install-connect-ubuntu?view=sql-server-ver16](https://docs.microsoft.com/en-us/sql/linux/quickstart-install-connect-ubuntu?view=sql-server-ver16)


Import the public repository GPG keys:(run these commands in terminal)


```sh
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
```

This command show response with OK.

### image21

Register the SQL Server Ubuntu repository:

```sh
sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/20.04/mssql-server-preview.list)"
```


### image22

Run the following commands to install SQL Server:
```sh
sudo apt-get update
```

```sh
sudo apt-get install -y mssql-server
```


### image23

After the package installation finishes, add passwords.
```sh
sudo /opt/mssql/bin/mssql-conf setup
```

### image24

Add 2 for developer package.
Then add password for mssql server.

Once the configuration is done, verify that the service is running:
```sh
systemctl status mssql-server --no-pager
```

### image25

Install the SQL Server command-line tools

To create a database, you need to connect with a tool 

```sh
sudo apt-get update
```

```sh
sudo apt install curl
```
 

### image26

Import the public repository GPG keys.
```sh
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
```


### image27

Register the Ubuntu repository.
```sh
curl https://packages.microsoft.com/config/ubuntu/20.04/prod.list | sudo tee /etc/apt/sources.list.d/msprod.list
```

Update the sources list and run the installation command with the unixODBC developer package.

```sh
sudo apt-get update 
```

```sh
sudo apt-get install mssql-tools unixodbc-dev
```

### image28

You can update to the latest version of mssql-tools using the following commands:

```sh
sudo apt-get update
```

```sh
sudo apt-get install mssql-tools
```
 

For interactive sessions, modify the PATH environment variable in your ~/.bash_profile file with the following command:

```sh
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
```


For non-interactive sessions, modify the PATH environment variable in your ~/.bashrc file with the following command:
```sh
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
```
### Connect locally

```sh
sqlcmd -S localhost -U sa -P '<YourPassword>'
```


If error occurs then follow the link



[https://hackthestuff.com/article/error-resolved-sqlcmd-command-not-found#:~:text=But%20instead%20of%20connecting%20with,check%20mssql%2Dtools%20is%20installed](https://hackthestuff.com/article/error-resolved-sqlcmd-command-not-found#:~:text=But%20instead%20of%20connecting%20with,check%20mssql%2Dtools%20is%20installed)


Or commands

```sh
sudo apt-get install mssql-tools
```

```sh
sudo ls /opt/mssql-tools/bin/sqlcmd*
```

```sh
sudo ln -sfn /opt/mssql-tools/bin/sqlcmd /usr/bin/sqlcmd
```


### Backup &  RESTORE DATABASE

### For Backup Database:


Using this command:

```sh
sqlcmd -S localhost -U SA -Q "BACKUP DATABASE ncdev2 TO DISK = N'/var/opt/mssql/data/demodb.bak' WITH NOFORMAT, NOINIT, NAME = 'demodb-full', SKIP, NOREWIND, NOUNLOAD, STATS = 10"
```


```sh
sqlcmd -S localhost -U SA -P 'Adobe@11'-Q "BACKUP DATABASE ncdev2 TO DISK = N'/var/opt/mssql/data/ncdev2.bak' WITH NOFORMAT, NOINIT, NAME = 'demodb-full', SKIP, NOREWIND, NOUNLOAD, STATS = 10"
```
### image29

### For Restore Database:


Using this command:

```sh
RESTORE DATABASE [db_name] FROM DISK = '/var/opt/mssql/data/demodb.bak'
```

```sh
WITH RECOVERY
```


```sh
GO
```


Reference

[db_name] -> Is the database name.
Demodb.bak -> Is the backup file name.

### BACKUP AND RESTORE DATABASE IN UBUNTU 20.04

### BACKUP:

first you must be in the context of that database you want backup for

```sh
BACKUP DATABASE database_name TO DISK = N'/var/opt/mssql/data/file_name.bak' WITH NOFORMAT, NOINIT, NAME = 'demodb-full', SKIP, NOREWIND, NOUNLOAD, STATS = 10
```

### RESTORE:

```sh
USE master
```

```sh
RESTORE DATABASE ncdev2_backfile FROM  DISK = N'/var/opt/mssql/data/ncdev2backfile1.bak' WITH  FILE = 1, MOVE N'ncdev2' TO N'/var/opt/mssql/data/ncdev2_backfile.mdf', MOVE N'ncdev2_log' TO N'/var/opt/mssql/data/ncdev2_backfile_log.ldf', NOUNLOAD, REPLACE, STATS = 1
```

Database name = ncdev2_backfile
bak file name = ncdev2backfile1.bak
use (ncdev2_backfile.mdf) for ncdev2
use (ncdev2_backfile_log.ldf) for ncdev2_log


### After mssql/Mysql set up now Adding data sources in the Administrator

### MSSQL SERVER

first of all enter into mssql server using below command

```sh
/opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P "Adobe@11"
```

-u: use msSQL server username batana hai e.g: SA

SELECT Name from sys.databases-p: use msSQL server password eg: "Adobe@11"


symbol "1>" that confirms your presence in MS SQL Server

Commands:
to create a new database


```sh
CREATE DATABASE database_name;
```

to shoe list all databases
```sh
SELECT Name from sys.databases;
```

next step is to connect datasource ko database in coldfusion administrator

### image30

Add data source name add select the database.
Then press the add button.
### image31



Then add the database name .
here add user name and password from msSQL server's credential
i.e
Database: new created databasename
server:locahost
Username: SA
Password: Adobe@11 

### image32


### MYSQL SERVER

open MySQL workbench 
CREATE DATABASE database_name;
Commands:
to create a new database


```sh
CREATE DATABASE database_name;
```

to shoe list all databases
```sh
SELECT Name from sys.databases;
```

next step is to connect datasource ko database in coldfusion administrator
### image33

select MySQL in Driver and click on add
### image34

complete all fields using username, severe, port from MySQL workbench
### image35
 
in work bench right click on user and then click on edit ,a dialog box will open from where you get all required details
### image36

Password : use password that was used to create Mysql setup 

### ERROR BY YOUR LUCK 
### image37

Solution:

[https://community.adobe.com/t5/coldfusion-discussions/mysql-jdbc-driver-for-coldfusion-2021-release/td-p/11727514](https://community.adobe.com/t5/coldfusion-discussions/mysql-jdbc-driver-for-coldfusion-2021-release/td-p/11727514)


### Steps to download and install:
1) Go to

[https://dev.mysql.com/downloads/connector/j/](https://dev.mysql.com/downloads/connector/j/)


Select Operating System: Platform Independent,
then click on "Download" button for "Platform Independent (Architecture Independent), ZIP Archive".

2) To download directly, click on "No thanks, just start my download". This will trigger the download of the file mysql-connector-java-8.0.22.zip.

3) Unzip the downloaded file. move mysql-connector-java-8.0.30.jar to /opt/ColdFusion2021/cfusion/lib/

Command to move file:

```sh
 sudo mv -f -i mysql-connector-java-8.0.30.jar /opt/ColdFusion2021/cfusion/lib/
```

4) Restart ColdFusion 2021



### LUCEE INSTALLATION

Follow this link

[https://acoderslife.com/posts/default/id/Setting-up-Apache-and-Lucee-on-Ubuntu-Server.htm](https://acoderslife.com/posts/default/id/Setting-up-Apache-and-Lucee-on-Ubuntu-Server.htm)


Once you have Ubuntu up and running, you'll want to get it up to date with the following commands.
```sh
sudo apt update && sudo apt upgrade -y
```

If you are interested in automatic updates for Ubuntu Server, you can use the following command to set that up.

```sh
sudo apt install unattended-upgrades
sudo dpkg-reconfigure unattended-upgrades
```

When prompted about installing important updates, just hit enter to select Yes.

Next, you'll need to install a couple of packages (or at least apache2). You don't really need axel, you could just use curl. Axel, however, is a download accelerator and will download files from most places much faster.



```sh
sudo apt install axel apache2
```

Once apache is installed, you should be able to open a browser and go to http://[server ip address] and see the default apache2 page.

Next, you will need to download the Lucee linux installer, set the appropriate permissions and run it to start the installation.


```sh
mkdir ~/downloads
```

```sh
cd ~/downloads
```

```sh
axel https://cdn.lucee.org/lucee-5.3.4.080-pl0-linux-x64-installer.run
```

```sh
chmod 744 ./lucee-5.3.4.080-pl0-linux-x64-installer.run
```

```sh
sudo ./lucee-5.3.4.080-pl0-linux-x64-installer.run --mode text
```

The last command will start the Lucee installation and ask you a number of questions. Most of the defaults are just fine for our purposes but you'll need to enter the admin password when prompted and, likely, increase the default heap sizes (though not entirely necessary).


Password: Adobe@11

Navigation link to test: [http://localhost:8888/lucee/admin/server.cfm](http://localhost:8888/lucee/admin/server.cfm)

Once the Lucee installer is complete, you can open a browser and navigate to http://[server ip address]:8888. You should see the Lucee welcome screen. Now that Lucee is installed, you have two admin contexts; one for the server context (http://[server ip address]:8888/lucee/admin/server.cfm) and one for the web context (http://[server ip address]:8888/lucee/admin/server.cfm).

When you log into the server context, the overview page will inform you of any updates you might need to install.

The default apache page is located in the default webroot at /var/www/html. You can drop your files in that directory or edit /etc/apache2/apache2.conf and /etc/apache2/sites-available/000-default.conf to change references to "/var/www/html" to your new directory or add a second site.

Here is a quick way to test out CF in the existing webroot.


```sh
sudo touch /var/www/html/index.cfm
echo "<cfscript>dump(server)</cfscript>" | sudo tee -a /var/www/html/index.cfm
```

Now create datasource on lucee server


After this run index.cfm that is on root  [http://localhost:8888/](http://localhost:8888/)
Root address for lucee

```sh
opt/lucee/tomcat/webapps/ROOT
```

If there is an error about insufficient permission

vs code permissions for folder
cd /path/to/my/files

```sh
chown -R $USER:$USER 
```


### COMMANDS TO RUN COLDFUSION SERVER AND TO ENTER IN DATABASE IN TERMINAL:


commands
### Start Coldfsuion
```sh
cd /opt/ColdFusion2021/cfusion/bin
```

```sh5
sudo ./coldfusion start
```

### Stop Coldfsuion

```sh
cd /opt/ColdFusion2021/cfusion/bin
```

```sh
sudo ./coldfusion stop
```
Enter into Database

```sh
/opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P "Adobe@11"
```

Then use Database:

```sh
use ncdev2
```

```sh
go
```

