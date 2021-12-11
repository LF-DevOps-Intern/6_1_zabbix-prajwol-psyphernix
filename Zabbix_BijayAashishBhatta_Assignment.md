1. **Installing Zabbix server on the Virtual Machine:**
	
	$ sudo wget https://repo.zabbix.com/zabbix/5.0/ubuntu/pool/main/z/zabbix-release/zabbix-release_5.0-1+focal_all.deb
	$ sudo dpkg -i zabbix-release_5.0-1+focal_all.deb
	$ sudo apt update
	$ sudo apt install zabbix-server-mysql zabbix-frontend-php zabbix-apache-conf zabbix-agent
	$ mysql -uroot -p
	mysql> create database zabbix character set utf8 collate utf8_bin;
	mysql> create user zabbix@localhost identified by 'password';
	mysql> grant all privileges on zabbix.* to zabbix@localhost;
	mysql> quit;
	$ sudo zcat /usr/share/doc/zabbix-server-mysql*/create.sql.gz | mysql -uzabbix -p zabbix
	$ sudo vim /etc/zabbix/zabbix_server.conf
	$ sudo vim /etc/zabbix/apache.conf
	$ sudo ystemctl restart zabbix-server zabbix-agent apache2
	$ sudo systemctl enable zabbix-server zabbix-agent apache2
	
	![image](https://user-images.githubusercontent.com/34814966/145663590-b5088ece-98cb-45bc-8b33-d78bc3fbca8a.png)
	![image](https://user-images.githubusercontent.com/34814966/145663682-f2e0fe54-048f-46c0-ad95-d8dc50fe0088.png)

2. **Screenshot of Running Zabbix Server service, Database config parameter in server config file, and
Server Dashboard:**


3. **Installing Latest Zabbix Agent on VM or host machine or server itself to fetch logs:**

