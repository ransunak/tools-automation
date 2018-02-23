# This Project consists of Installation of Artifactory, Mysql and Nginx for reverse proxy in RHEL-7

--Project Structure
.
 |
  - artifactory-install-configure.yml
  - inventory
  - setup.sh
  - roles
    |
      - vars
         - default.yml
      - mysql
         - tasks
            - install_mysql.yml
            - main.yml
         - vars
            - default.yml
       - artifactory
          - tasks
            - install_artifactory.yml
            - main.yml
           - templates
             - db.properties
        - nginx_config
          - tasks
            - main.yml
            - install_nginx.yml
            - create_certs.yml
          - templates
            - nginx.conf
          
 
 # Discription on how to run this project to Install and Configure Artifactory
 
 Scenario - 1
  - If both Artifactory and Mysql Database were to be installed in one machine then Edit the inventory file and default.yml file inside vars
  Ex: 1) Inventory file
    <mysql>
    <IP> ansible_user=<user> ansible_ssh_private_key_file=<Key_Path>
    <application>
    <IP> ansible_user=<user> ansible_ssh_private_key_file=<Key_Path>
  
   2) default.yml file
      Mysql_root_password: <root_password>
      DB_USER: root
      Mysql_Database: <database_name>
      Mysql_Username: <database_user>
      Mysql_Password: <database_user_password>
      Artifactory_Host: <Artifactory_IP>
      Mysql_Host: <Mysql_Host_IP>
      Artifactory_DNS: <DNS_NAME>
      nginx_cert_path: /etc/nginx/ssl/nginx.crt
      nginx_key_path: /etc/nginx/ssl/nginx.key
      
Once the above two files changes run the setup.sh 
  
   Scenario - 2
  - If both Artifactory and Mysql Database were to be installed in different machine then Edit the inventory file and default.yml file inside vars
  Ex: 1) Inventory file
    <mysql>
    <Mysql_IP> ansible_user=<user> ansible_ssh_private_key_file=<Key_Path>
    <application>
    <Artifactroy_IP> ansible_user=<user> ansible_ssh_private_key_file=<Key_Path>
  
   2) default.yml file
      Mysql_root_password: <root_password>
      DB_USER: root
      Mysql_Database: <database_name>
      Mysql_Username: <database_user>
      Mysql_Password: <database_user_password>
      Artifactory_Host: <Artifactory_IP>
      Mysql_Host: <Mysql_Host_IP>
      Artifactory_DNS: <DNS_NAME>
      nginx_cert_path: /etc/nginx/ssl/nginx.crt
      nginx_key_path: /etc/nginx/ssl/nginx.key
      
Once the above two files changes run the setup.sh 
    
    
    
    
  
  
 
 
