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

**Uploading Objects to your S3 Bucket**

**Listing Objects in your S3 Bucket**

**Enable Versioning in your S3 Bucket**

**Uploading New Object Versions to your S3 Bucket**

**Listing Object Versions**

**Restoring Object Versions**

**Uploading HTML Files to your S3 Bucket**
* Create index.html and 404.html

**Enable Hosting in your S3 Bucket**

**Navigate your S3 Static Site**
* Check that endpoint shows index.html
* Check that not found pages shows 404.html

**Reference**
* [AWS S3 CLI Reference](https://docs.aws.amazon.com/cli/latest/reference/s3/)
