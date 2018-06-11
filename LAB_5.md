# Lab 5: RDS Getting Started

**Create A Security Group for DB**
* On EC2 service tab, on the left side of the screen, under the Network & Security options, select Security Groups.
* Create a New Security Group
  * Add a name for your security group (Ex. sg-fernando)
  * Select your VPC (the one created of Lab #2 )
  * Add a rule for port 3306 and source select the id of your instance security group

**Launching an RDS MySQL Instance**
* Go to your AWS Console > RDS Service > Instance > Launch DB Instance
  * Select Engine
    * Engine: MySQL
    * Edition: MySQL 5.6-compatible
  * Specify DB Details
    * DB Instance Class: db.t2.small
    * Multi AZ Deployment: No
    * DB Instance Identifier: Academy01 (use your own user)
    * Master username: Academy01 (use your own user)
    * Master password: (choose your own password)
    * Confirm password: (repeat your password)
  * Configure Advanced settings (Networking & Security):
    * VPC: select your VPC
    * Subnet group: select private subnet
    * Public accesible: No
    * VPC Security Group: select your db security group
  * Configure Advanced settings (Database options):
    * DB Cluster Identifier: Academy01 (use your own user)
    * Database name: wordpress
    * Leave rest values as default
  * Configure Advanced settings:
    * Leave the rest values as default
* Launch DB Instance
* Wait for your DB Instance to be ready

**Test Connection from EC2 to RDS using MySQL Client**
* Once your instance is ready click on it to see the details
* Look in the Connect section for the Endpoint 
* You will use it to test connection
```
mysql -u {your-user} -h {your-db-host} -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 15
Server version: 5.6.10 MySQL Community Server (GPL)

Copyright (c) 2000, 2018, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql>
```

**List your Databases**
* You can list the current databases with the following command
```
mysql> show DATABASES;
```
* It should show your wordpress db
```
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| wordpress          |
+--------------------+
4 rows in set (0.01 sec)
```

**Installing Wordpress on EC2 Instance**
* Install Wordpress in your EC2 Instance and use the wordpress db from RDS Instance

**Create a Snapshot of the RDS Instance**
* Select you RDS Instance
* At the right you will see a button for Instance actions
* Click on it and select Take snapshot
  * Snapshot name: Academy01-snapshot (Select your own user)
* Click in Take snapshot button
* Wait until the snapshot is completed

**Update your wordpress site**
* Do some updates like creating pages or posts

**Restore an RDS Snapshot**
* Go to your Instance and look for Details and copy the Resource ID, we are going to use it in following steps
* Go to your DB snapshot and select yours, click on Actions and select restore
  * DB Instance Identifier: Your DB Resource ID
  * Check that the rest of the values are the same as your instance
* Click in Restore DB Instance button
* Wait for the restored db to be ready

**Update DB Settings in Wordpress**
* Once your restored db is ready update the db details in wordpress
* Go to wordpress again and see the changes
