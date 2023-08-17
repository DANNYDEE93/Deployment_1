# Purpose of Deployment

* To deploy a web application using AWS Elastic Beanstalk.

# Description

This project began diagramming the plan for my deployment in Draw.io including how I would use **GitHub**, **Jenkins**, and **AWS Elastic Beanstalk**. I continued to plan and build within a previously created Jenkins account by my instructor. Jenkins allowed me to create and test my deployment in a staging environment to ensure that it would return a 200 response from the server once deployed. Once my build passed the test phase in Jenkins, I created IAM roles and an EC2 instance through Elasticn Beanstalk. This allowed AWS access with the necessary permissions to update and launch my deployment through the IAM roles of **AWSElasticBeanstalkWebTier** and  **AWSElasticBeanstalkMulticontainerDocker**. Finally, the EC2 instance createed an applicable production environment to deploy my web applicaiton successfully. 

### Below you will find the necessary steps that I took to test and deploy my web applicaiton, as well as some drawbacks that I was able to rectify along the way: 

1. Diagram the plan for deployment on Draw.io:

/assets/images/planfordeployment1.png



Log into GitHub account
Create new GitHub repository
Create "Documentation.md" file to record the staging and production environment of deployment
Open Kura Labs c4 Deployment-1 repository
Press the "Code" tab and download files from Kura Labs repository
Unzip Kura Lab files through terminal 
Upload Kura Lab repository files into new GitHub repository created in Step 3
Sign into Instructors Jenkins account with provided login
Press "New Item" tab to create new pipeline build
Name pipeline "First name, Last name initial"
Select Pipeline script from SCM
Choose Git in the dropdown from SCM
Go back to newly created GitHub repository and copy the HTTP code
Paste code into Repsitory line in Jenkins
Go back to your GitHub and press profile picture
Select "Settings"-->"Developer Settings"-->"Personal Access Tokens"--> "Tokens(classic)"
Select "Generate new token"-->"Generate new token (classic)"-->Sign into GitHub if prompted
Create note description-->Select scopes: "repo" and "admin repo" to give full access to repository.
Generate token--> Copy and past link into passwork line in Jenkins
Continue on Jenkins-->Add token associated with repository--> Select main branch
Submit to generate build and select "Build Now" and pass staging environment in Jenkins
My multiple attempts to download onto Jenkins were unsuccessfuly because my copied Jenkinsfile was saved as a .txt file that was blocking Jenkins from reading the file's code properly. Once I deleted ".txt off the file, my build passed the test stage on Jenkins
Create zip file folder through terminal or in your File Explorer to compress your GitHub repository. This new compressed zip file should not exceed 500 MB and should not include parent folder from your original repository to ensure that all characters in file are configured correctly in Elastic Beanstalk:
Select files within the downloaded file of your repository and transfer them into a new compressed zip folder. This ensures that the files are zipped to Elastic Beanstalk's standards 
After checking the console output responses and passing the test phase in Jenkins, you can go on to creating Roles and the Python Url Shortener through AWS Elastic Beanstalk
Sign into AWS with appropriate Account ID, IAM user name, and password 
Select "Roles" in Dashboard--> Click "Create role"--> Select "AWS service" for trusted entity type--> Under the dropdown for AWS Services: Select "Elastic Beanstalk"--> Select Customizable option under cases to give Elastic Beanstalk permission to manage AWS resources of your deployment--> Click Next--> Click Next--> Enter "AWS-Elasticbeanstalk-service-role" in Role name--> Create Role
To create a second role: Click Create Role--> Select "AWS service" for trusted entity type--> Click "EC2" under common use cases--> Click Next--> Under Permission policies: Select "AWSElasticBeanstalkWebTier" and "AWSElasticBeanstalkMulticontainerDocker"--> Click Next--> Enter "Elastic-EC2" in Role name field--> Click "Create Role"
These roles allow the instances in your web server environment to access and upload necessare files and grants permissions for Amazon Elastic Container Service to organize and cluster task within container environments.
Create and deploy a Python URL shortener on AWS Elastic Beanstalk 
Select "Create Application"--> Name application name "URL-shortener"--> Select "Python" in Platform dropdown--> Select "Python 3.9 running on 64bit Amazon Linux 2023" in Platform branch dropdown-->Select "Upload your code"--> Type "V1" in version label field--> Choose and upload the compressed zip file of your repository-->Click Next
Select "ElasticEC2" in EC2 instance profile dropdown--> Click Next--> Select default VPC in VPC dropdown--> Select "us-east-1a" availability zone--> Click Next--> Select "General Purpose (SSD)" in Root Volume type drop down--> Change the size field to 10GB-->Select ONLY "T2.MICRO" under "Instance Types" and deselect any other choices--> Click Next--> Click Next--> Click Submit
The URL shortener reduces the number of characters in a URL so that it is easier for Elastic Beanstalk to read, remember, and share your web service and application. AWS Elastic Beanstalk makes it easier for developers to quickly depoly and manage these applications.
Upload and Deploy your compressed zip file on Elastic Beanstalk. You will know that you passed once the health staturs is "OK" and you get a response that your deployment has uploaded successfully to your EC2 instance.
Although, I downloaded a zip file from my repository. This file was not uploading succesfully and the health of my deployment kept changing to "Degraded" because it was not compressed enough to Elastic Beanstalk requirements. After multiple attempts, I found out that I needed to create a completely new compressed zip file with only the files within the downloaded zip file. Only then, was i able to complete my first successful deployment. 
