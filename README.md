**Problems that I faced during installation of wamp:**
***
1. **Problem  1**: Apache not working.  
**Solution 1**: Goto `wamp icon ->Apache -> service ->test port 80`. This will show you whether your port 80 is free or is used by some other application, most probably Skype. In that case either stop Skype through control panel.  
 Or goto `wamp icon ->Apache ->httpd.conf ->change 80 to 8080` (3 changes in this file).  
Now, restart wamp. 

2. **Problem 2**: MySql not working or showing error cannot run for 'root'@'localhost'.  
**solution 2:** Goto wamp icon ->mysql ->mysql console. Then type the following command:  
`use mysql;  
update user set password=PASSWORD("mynewpassword") where User='root';  
flush privileges;  
quit`  
Then goto c:/wamp/apps/config.inc.php  
Change:  `$cfg['Servers'][$i]['password'] = 'mynewpassword';` and `$cfg['Servers'][$i]['auth_type'] = 'cookie';`  
3. **Problem 3:** Wamp Error 407:Forbidden: You dont have access to phpmyadmin at this server  
**Solution3:** goto C:/wamp/alias/phpmyadmin.conf  
change  
`Order Allow,Deny  
Deny from all  
Allow from 127.0.0.1  
by  
Order Allow,Deny  
Allow from all `  
to  
`<Directory c:/wamp/apps/phpmyadmin3.3.9/>`
    `Options Indexes FollowSymLinks MultiViews`
   `AllowOverride all`
        `Order Allow,Deny`
	
	`Allow from all`
`</Directory>`


4. New **AMPP**
 first this : https://stackoverflow.com/questions/47013891/apache-doesnt-start-in-ampps-on-ubuntu
 second this : https://www.youtube.com/watch?v=KBxhdAj5jDk
   
cd /path/to/Ampps/mysql/bin
sudo killall mysqld
cd /path/to/Ampps/mysql/bin
./mysqld --skip-grant-tables


         
