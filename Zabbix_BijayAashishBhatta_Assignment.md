1. **Installing Zabbix server on the Virtual Machine:**
	
		$ sudo wget https://repo.zabbix.com/zabbix/5.0/ubuntu/pool/main/z/zabbix-release/zabbix-release_5.0-1+focal_all.deb
		$ sudo dpkg -i zabbix-release_5.0-1+focal_all.deb
		$ sudo apt update
		$ sudo apt install zabbix-server-mysql zabbix-frontend-php zabbix-apache-conf zabbix-agent php-mysql
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
	
	![image](https://user-images.githubusercontent.com/34814966/145665092-062087c6-95db-49e7-a7bc-9eb5b9d0954e.png)

	![image](https://user-images.githubusercontent.com/34814966/145663682-f2e0fe54-048f-46c0-ad95-d8dc50fe0088.png)

2. **Screenshot of Running Zabbix Server service, Database config parameter in server config file, and
Server Dashboard:**

		$ sudo systemctl status zabbix-server
		
![image](https://user-images.githubusercontent.com/34814966/145665213-a68f87d7-2195-4a1e-b435-0d72aad26e81.png)

		$ cat /etc/zabbix/zabbix_server.conf
		
![image](https://user-images.githubusercontent.com/34814966/145665250-3cd915a0-454e-4cc6-b9e1-8e6c024b8ffe.png)

![image](https://user-images.githubusercontent.com/34814966/145665933-5eefeedf-6039-427d-ba0c-30792f8f7dbf.png)

3. **Installing Latest Zabbix Agent on VM or host machine or server itself to fetch logs:**

	![image](https://user-images.githubusercontent.com/34814966/145667753-d0d0802b-a2ad-46aa-b9f8-48c3c3409815.png)

