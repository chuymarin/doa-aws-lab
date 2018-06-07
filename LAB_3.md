
# Lab 3: EC2 Getting Started

**Create EC2 Security Group**
* On EC2 service tab, on the left side of the screen, under the Network & Security options, select Security Groups. 
* Create a New Security Group  
  * Add a name for your security group (Ex. sg-fernando)
  * Select your VPC (the one created of Lab #2 )
  * Add a rule for port 22 and port 80

**Launching EC2 Instanaces**
* Under EC2 service tab, select the option "Launch Instance"
  * Step 1: Choose AMI
    * Select Amazon Linux AMI 
  * Step 2: Choose instance type
    * Use t2.micro (free tier :D )
  * Step 3: Configure instance details
    * Network: use your own VPC 
  * Step 4: Add Storage
    * Use default storage (8 GIG EBS)
  * Step 5: Add Tags
     * Add a tag with the following values: 
     * Key = Name
     * Value = YourName-host
  * Step 6: Cnfigure Security Group
      * Select your Security group (previous step)
* NOTE: please use alan.pem as key for your new host.  
* LAUNCH YOUR AWS INSTANCE!

**Install Nginx in EC2 Instance**
* Access by SSH to your new EC2 instance
  * sudo yum install nginx 
  * sudo yum install php php-fpm
  * Create basi vhost in nginx
  * create a file under /etc/nginx/sites-enabled/random-name-vhost-conf
  * add this to your vhost
```
server {
    listen 80 default_server;
    listen [::]:80 default_server;

    root /var/www/html/CHANGE-THIS-FOLDER;
    index index.html;

    server_name _;

    location / {
        try_files $uri $uri/ =404;
    }
}
```
    * Add a random file in /var/www/html/FOLDER
    * restart nginx
    * service nginx restart
* Confirm you can access yo your host using port 80 by web browser. You should see your file content.

**Add New Rule to EC2 Security Group**
* For port 80
* Verify that Nginx Service is available

**Install MySQL Client**
* sudo yum install mysql-server mysql
* confirm access and correct installation by typing 
```
mysql - this will give you access to MySLQ console
chkconfig mysqld on
```

**Create an AMI**
* Under EC2 service tab
  * Select your EC2 server
  * Right click on your instance, on the Image tab, select "Create AMI"
  * Add an specific name for your AMI
  * IMPORTANT!! SELECT "No reboot" option. 
  * Create Image

**Terminate your EC2 Instance**
* Under EC2 service tab
  * Select your EC2 server
  * Right click on your instance, on the "Instance State" tab, select Terminate
  * After confirming the termination, your instance will be erased. 

**Launch a new EC2 Instance from your AMI**
* Under EC2 service tab, select the option "Launch Instance"
* Step 1: Choose AMI
  * Select your AMI name for using it as a base Image for your new EC2 server. 
* Step 2: Choose instance type
  * Use t2.micro 
* Step 3: Configure instance details
  * Network: use your own VPC 
* Step 4: Add Storage
  * Use default storage 
* Step 5: Add Tags
  * Add a tag with the following values: 
    * Key = Name
    * Value = YourName-host
* Step 6: Cnfigure Security Group
* Select your Security group 

**Verify Config**
* Once your instance is launched and all the check are green. 
  * Access by SSH to your instance
  * Confirm all services are up and running, if not, start them (nginx & mysql)
  * Confirm you still have access to port 80 and you can see your file's content. 
