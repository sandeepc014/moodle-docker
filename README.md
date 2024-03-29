﻿Docker For Moodle

Introduction:

This documentation provides information on how to clone MOODLE environment into local linux and windows machine from docker compose. The docker compose files includes all dependencies which require to run MOODLE application on the Linux  & Windows environment by cloning the Docker compose files from the version control system to the host machine, with minimal effort using containerization platform with a single command, you can spin up and stop new  MOODLE containers on your machine


Package Installed on Docker images:


Server OS : Ubuntu 22.04.1 LTS
PHP Version : PHP 8.0
MySQL Version :  5.7.27
Additional Packages : git vim net-tools 


MOODLE application URL: http://localhost


                               PORTS:
                                 NGINX: 80
                                 MYSQL: 5073
                                 PHPMYADMIN: 5074
                                 MAILHOG: 5076


Note: Moodle application work port “80” if your machine using this port please stop the respective service and start moodle docker



**Procedure of MOODLE Docker For UBUNTU:**


1. Clone MOODLE Docker project folder from bitbucket to in your machine


BITBUCKET URL: git clone git@bitbucket.org:linkstreet/moodle-docker.git
                                                                  
2. Open .env file and provide moodle & moodledata project folder path 
     
3. Type command called docker-compose up -d  and it creates MOODLE docker container and make application run and up
                     
4. Open moodle config.php and update database details


                                  $CFG->dbtype        = 'mysqli';
                                  $CFG->dbhost        = 'moodle-mysql'
                                  $CFG->dbname        = 'moodle';
                                  $CFG->dbuser        = 'root';
                                  $CFG->dbpass        = 'root'
                                  $CFG->dataroot  = '/var/www/moodledata';

5. Once application up browse URL http://localhost:5074  for phpmyadmin to import/create MOODLE database with below credentials. 
                                                       
                                  Server: moodle-mysql
                                  Username: root
                                  Password: root
                                               
6.  Once import database and type below URL in your browser and follow installation steps of moodle 
                      
                                  Moodle Application URL: http://localhost
                                  Moodle PHPMYADMIN: http://localhost:5074
                                  Moodle  MAILHOG: https://localhost:5076
                       
 
**Procedure of MOODLE Docker For Windows:**


1. Window machine requires Docker tool software to run docker commands in the application and please find below link to download


                                  Link: https://download.docker.com/win/stable/DockerToolbox.exe


2. Run downloaded .exe file to install application in windows machine

3. Once setup finish open Docker application on the desktop by clicking the icon
                                          
4. Please wait a few minutes  to create a virtual machine for docker application

5. Once finished, it will create a virtual machine IP as per above screenshot note down the same.


6. Here we Clone MOODLE docker files in your windows followed path    
D:\moodle-docker                  
               
                                  BITBUCKET URL: git clone git@bitbucket.org:linkstreet/moodle-docker.git                         
    
7. Go to the cloned  MOODLE-docker folder and  open .env file and enter moodle and moodledata folder path 
                     
                                  Note:  If your project folder exist in other drive such D, E please follow 14th steps to mount folder 
               
8. Open moodle config.php and update database details


                                  $CFG->dbtype        = 'mysqli';
                                  $CFG->dbhost        = 'moodle-mysql'
                                  $CFG->dbname        = 'moodle';
                                  $CFG->dbuser        = 'root';
                                  $CFG->dbpass        = 'root'
                                  $CFG->dataroot  = '/var/www/moodledata';


9. Now it time to run docker command to spin up application by using command as follows
                
                                  CMD:  docker-compose up -d

10. Once command runs it pull images and  create docker container for the MOODLE applications and will take a few minutes 

11.  Once application up browse URL http://192.168.99.100:5074  for phpmyadmin to import MOODLE with below credentials and click Go to phpmyadmin dashboard and restore database into it with name of “MOODLE”
                                                          

                                  Server: moodle-mysql
                                  Username: root  
                                  Password: root
                              
                        
12.  Once import database into the phpmyadmin with MOODLE label and type below URL in your browser follow moodle installation process till app gets installed
                   
                                  Application URL: http://192.168.99.100
                                  PHP MY ADMIN: http://192.168.99.100:5074
                                  MAILHOG:  http://http://192.168.99.100:5076
                     

14.  How to share folder in Virtual box if project folders are exist in other drive


                                  Open VirtualBox
                                  Right-click your VM, then click Settings
                                  Go to Shared Folders section
                                  Add a new shared folder
                                  On Add Share prompt, select the Folder Path in your host that you want to be accessible inside your VM.
                                  In the Folder Name field, type shared
                                  Uncheck Read-only and Auto-mount, and check Make Permanent 
                                  Save & Start your VM

**Google Drive Documentation Link:** https://docs.google.com/document/d/1v9K4uAu7YYKvt8k2BwnwM-rycCm5lMY6XCJJGQvFteE/edit# 
