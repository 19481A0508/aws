the steps to create an Amazon EC2 cloud virtual machine instance (t2.micro free tier Ubuntu Linux) inside a VPC and subnet, deploy a S3 static website (Hello world) using Python and install Nginx in EC2 instance using remote execution:

1.Create a VPC and a subnet
2.Log in to your AWS console and navigate to the VPC dashboard.
3.Click on "Create VPC".
4.Once the VPC is created, move to "Subnets" section and click on "Create Subnet."
5.The subnet in the VPC just got created.
6.Launching an EC2 instance:
Navigate to the EC2 dashboard and click on "Launch Instance."
Select "Ubuntu Server 22.04 LTS" as the Amazon Machine Image and "t2.micro" as the instance type.
In the "Configure Instance Details" section, select the VPC and subnet created earlier.
Leaving the default settings for the remaining sections and launch the instance.
7.Connect to the EC2 instance
8.Once the instance is launched, connect to it using SSH.
9.install python boto3 using pip install boto3 command.
10.find the public IP address of the instance in the EC2 dashboard.
11.Deploy a S3 static website using Python
12.Create a new file using the command "nano index.html" and add the HTML code for "Hello world" website.
Code used to host website

import boto3
s3 = boto3.resource('s3')
bucket_name = 'yochana-bucket'
bucket = s3.Bucket(bucket_name)
bucket.create()
bucket.upload_file('index.html', 'index.html')
print('Website deployed to S3 bucket: ', bucket_name)

Run the above Python script using the command "python deploy_website.py" to deploy website to the S3 bucket.


14.Install Nginx in EC2 instance using remote execution.


URL of the website hosted: 
https://helloworld-com.s3.ap-south-1.amazonaws.com/index.html
