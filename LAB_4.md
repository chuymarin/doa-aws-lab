# Lab 4: S3 Getting Started

**Launch your EC2 Instance from AMI**
* Go to AWS Management Console and select EC2 Service
* Go to Images > AMI's and select your AMI
* Click ACtions button and click in Launch
* Proceed with the launch wizard and launch your instance

**Adding IAM Role to your EC2 Instance**
* Go to EC2 > Instances and select your created instance
* Click on Actions button and select Instance Settings > Attach/Replace IAM Role
  * IAM Role: Select your previously created IAM Role
* Click Apply button
* Connect to your instance using SSH

**Configuring AWS CLI**
* Execute the following command: `aws configure`
* Leave all values as default by hitting enter expect for the Default region name
* and select the region where your instance is running
```
AWS Access Key ID [None]:
AWS Secret Access Key [None]:
Default region name [None]: us-east-1
Default output format [None]:
```

**Listing S3 Buckets**
* List all the buckets in S3 with the following command
```
aws s3 ls
```
* You will see a list of the current S3 buckets int the selected region

**Creating S3 Bucket using AWS CLI**
* To create a new bucket use the following command: `aws s3 mb s3://bucket-name`
* mb stands for make bucket, and bucket names must be unique across all existing bucket names in Amazon S3
* Execute the following command to create your S3 bucket, replace the number with your own
```
aws s3 mb s3://mdc-doa-academy-01
```
* It will show you this output
```
make_bucket: mdc-doa-academy-01
```
* We use bucket names with prefixes to be sure that our bucket is unique across all buckets in S3
* You can list all the buckets again to verify that your bucket is created
* Note: from now on, change bucket-name with your own bucket-name

**Uploading Objects to your S3 Bucket**
* Create an s3 directory in the home of your instance's user and cd into it
* Create myfile.txt file and write your name on it
* We are going to upload this file to your S3 Bucket
* Execute the following command to upload your file:
```
aws s3 cp myfile.txt s3://bucket-name/myfile.txt
```
* And the output will be similar to:
```
upload: ./myfile.txt to s3://bucket-name/myfile.txt
```

**Listing Objects in your S3 Bucket**
* Now list your S3 Bucket Objects
* Execute the following command:
```
aws s3 ls s3://bucket-name
 ```
 * And you will see a list of your current objects

**Enable Versioning in your S3 Bucket**
* Now go to AWS Console > S3 Service
* Search your bucket and click on it
* Go to Properties tab and click in Versioning
* Select Enable and click Save button

**Uploading New Object Versions to your S3 Bucket**
* Modify the contents of your file
* And upload it again 
* Repeat this step 1 or 2 times more, so we can have more versions

**Listing Object Versions**
* Go to your S3 bucket in Overview tab
* You will see that there is a Versions text, select show
* And you will see multiple versions of your file

**Restoring Object Versions**
* Restoring versions works by uploading previous versions or deleting latest version, [see more](https://docs.aws.amazon.com/AmazonS3/latest/dev/RestoringPreviousVersions.html)
* Select the Latest Version of your file
* Click in More button and select Delete
* Now download the latest file to your instance as follow:
```
aws s3 cp s3://bucket-name/myfile.txt myfile.txt
```
* And the output will be similar to:
```
download: s3://bucket-name/myfile.txt to ./myfile.txt
```
* Cat your file to see that it is available but with a previous version

**Creating files for a static site**
* Create an index.html file with the following content:
* Tip: change where it says {your-name-here} with your name
```
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>Welcome to my site | {your-name-here}</title>
</head>
<body>
<script src="https://code.jquery.com/jquery.min.js"></script>
<link href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/css/bootstrap.min.css" rel="stylesheet" type="text/css" />
<script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/js/bootstrap.min.js"></script>

  <h1>Hello My name is {your-name-here}!</h1>
  <p>Welcome to my site.</p>
  
</body>
</html>
```
* Create an 404.html file with the following content:
```
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>JS Bin</title>
</head>
<body>
<script src="https://code.jquery.com/jquery.min.js"></script>
<link href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/css/bootstrap.min.css" rel="stylesheet" type="text/css" />
<script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/js/bootstrap.min.js"></script>

  <h1>404 - This is not the page you are looking for!</h1>
  <p>Look somewhere else.</p>
  
</body>
</html>
```
* Upload both files to your S3 bucket adding public read as follow:
```
 aws s3 cp index.html s3://bucket-name/index.html --acl public-read
 aws s3 cp 404.html s3://bucket-name/404.html --acl public-read
```

**Configure S3 Bucket as a website**
* Now execute the following command to configure your bucket as a website
```
aws s3 website s3://bucket-name/ --index-document index.html --error-document 404.html
```

**Navigate your S3 Static Site**
* Navigate to your bucket and select Properties tab
* Select Static website hosting
* And you will see and Endpoint, that is your website URL
* Open it and be sure that shows the index.html contents
* Add /something to the URL, and be sure that shows the 404.html contents
* Feel free to modify the look of your site, you can find useful docs in reference step!

**Reference**
* [AWS S3 CLI Reference](https://docs.aws.amazon.com/cli/latest/reference/s3/)
* [AWS S3 Restoring Previous Versions](https://docs.aws.amazon.com/AmazonS3/latest/dev/RestoringPreviousVersions.html)
* [Bootstrap Getting Started](https://getbootstrap.com/docs/4.1/getting-started/introduction/)

