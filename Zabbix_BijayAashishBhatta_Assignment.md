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

	![image](https://user-images.githubusercontent.com/34814966/145670453-2850b56d-f0a7-4095-aea0-f5f36998f7bf.png)

   		$ sudo usermod -aG syslog zabbix
		$ sudo chmod 644 /var/log/syslog
		
	![image](https://user-images.githubusercontent.com/34814966/145671091-ff82b845-a0e8-4c6d-8f8f-62a671b59f99.png)

	![image](https://user-images.githubusercontent.com/34814966/145672087-ccec03d3-b579-47ee-a93d-94e1d34a63dd.png)
	
	![image](https://user-images.githubusercontent.com/34814966/145672123-5fa535fb-70a7-4dfd-b179-6aa5af4fbb6e.png)

	![image](https://user-images.githubusercontent.com/34814966/145672143-ebb6fd42-ac4a-4bda-b50d-16881d5ab564.png)

	![image](https://user-images.githubusercontent.com/34814966/145672159-307b646a-3aeb-44a4-a097-d82177446a28.png)

	![image](https://user-images.githubusercontent.com/34814966/145672179-af57a511-ca15-4fa9-91d7-1a6fc812a8db.png)

	![image](https://user-images.githubusercontent.com/34814966/145672185-06ea5792-7d42-4dae-b4c6-501a5a905c83.png)

	![image](https://user-images.githubusercontent.com/34814966/145672208-51952637-713c-4afd-aa22-613dc6811af0.png)

	![image](https://user-images.githubusercontent.com/34814966/145672226-fa3edf49-966d-4a08-9fa8-5d219f676443.png)

	![image](https://user-images.githubusercontent.com/34814966/145672249-7d69bea3-b35f-4cee-b8da-1bab5bc5c0df.png)

	![image](https://user-images.githubusercontent.com/34814966/145672269-9aeed89e-dfbf-4db6-a412-29b715c5c083.png)

	![image](https://user-images.githubusercontent.com/34814966/145672302-6619f0c3-7f0d-42b7-8377-034ca7b234a4.png)

	![image](https://user-images.githubusercontent.com/34814966/145672309-b1357a38-e9f1-485a-be8c-c11d074cf5d4.png)
