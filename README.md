# MyCloudDrive Project

## Overview

MyCloudDrive is a cloud storage solution built on Amazon Web Services (AWS) infrastructure, utilizing AWS EC2 instances with FileCloud and Amazon S3 storage to create your own cloud drive.
This README provides an overview to set up your MyCloudDrive.

## Prerequisites

Before you begin, make sure you have the following:

- An AWS account with appropriate IAM permissions.
- AWS Access Key ID and Secret Access Key.
- Basic knowledge of AWS services.
- Follow this [video](https://www.youtube.com/watch?v=xBIowQ0WaR8) for the detailed steps

## Deployment Steps

### 1. Set Up Amazon S3 Bucket
- Navigate to S3 and create a new S3 bucket to store user files.
- Donot make any change in the bucket or file cloud wont be able to edit the bucket

### 2. Setup IAM policy
- create a new user
- assign the following permission to the user : [permissions](https://www.filecloud.com/supportdocs/fcdoc/latest/server/filecloud-administrator-guide/filecloud-site-setup/storage-settings/filecloud-managed-storage/iam-user-policy-for-s3-access)
- generate client secret key

### 2. Launch an AWS EC2 Instance
- Log in to your AWS Management Console.
- Navigate to EC2 and choose "Launch Instance."
- Select the FileCloud Amazon Machine Image (AMI).
- Choose an instance type. I recommend using a `t3.medium` instance for better performance. 
- Review and launch the instance, selecting or creating an SSH key pair.
- Connect to your instance using SSH.


### 3. Configure Your File Cloud
- Log into file cloud : https://portal.getfilecloud.com/ui/user/index.html#/sites/trial/community
- Follow these steps to set up file cloud : [link](https://www.filecloud.com/supportdocs/fcdoc/latest/server/filecloud-administrator-guide/installing-filecloud-server/installation/amazon-web-services-aws-installation)
- You will have to edit config file to change from local to amazons3, and rename the sample amazons3 file as mentioned in above link
- Login into the file cloud using the public url of your ec2 instance, the username is admin and password is your instance id (including i)
- in settings add the client key and secret from IAM
- mention bucket name and save

### 6. Security Considerations
- Secure your EC2 instance using AWS security groups and Network ACLs.
- Use SSL/TLS certificates to encrypt data in transit.

## Usage
- First create user from the admin panel
- You can access your cloud drive by navigating to your EC2 instance's public IP or DNS in a web browser.

## Acknowledgments

- Special thanks to Network Chuck for the tutorial : https://www.youtube.com/watch?v=xBIowQ0WaR8
