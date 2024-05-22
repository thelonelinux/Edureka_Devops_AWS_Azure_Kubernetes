# Edureka_Devops_AWS_Cloud
Learning about DevOps, mostly in Amazon AWS in the cloud

## Steps to get started
#### 1. Get an AWS free or Paid Account. For a Free or Paid Account You can check any YouTube videos, there it is explained.
#### 2. Once the account is created. You can start with the AWS Instance Creation. An instance is created on the Cloud, You can choose any OS, etc, and create an EC2 Instance. Steps you can check in Youtube
#### 3. Once the instance is created, connect that instance and open AWS CLI. It is usually like Ubuntu Terminal only if you have chosen Ubuntu as the OS when creating the instance. 
#### 4. Now we will install Jenkins, Jenkins are used to create PIPELINE(Sub-Jobs) for CI/CD. Jenkins is a third party for AWS, it is not pre-installed there. for that, you need to type some below commands. However, AWS has its own Jenkins-like features called, CodeCommit, CodeBuild, and CodeDeploy.
#### 5. The code commit is AWS GitHub like Bitbucket for Atlassian. But let's do Jenkins for now. As they are all paid service.
#### 6. Jenkins is free, but you have to use GitHub to get the latest code for deployment and build jobs. However, CodeCommit CodeBuild and CodeDeploy are paid services of AWS and we don't need GitHub or Jenkins if we have access to these services.
#### 7. CodeBuild, CodeCommit, and CodeDeploy services are accessible for free or paid only if you log in as an AMI user, instead of a root user, when logging into AWS.

----------------------------------------------
<br><br/>

## About installing Jenkins in Amazon EC2 Instance in Ubuntu Image.
* https://medium.com/@shahid199578/installing-jenkins-on-an-ec2-machine-d2e741a07785

Step 1: Create an EC2 Instance
create and connect to an EC2 instance. If you’re not familiar with how to create and connect to an EC2 instance, you can refer to “How to Create and Connect to an EC2 Instance,” for detailed step-by-step instructions. Once you have your EC2 instance ready, you can continue with the installation of Jenkins.

Step 2: Install Java
Jenkins is built on Java, so we need to install it first. Open a terminal and run the following command:

$$ sudo apt-get install openjdk-11-jre
To confirm that Java is installed correctly, check its version with:

$$ java --version
Step 3: Update the System
To ensure that your Ubuntu server is up to date, run the following command:

$$ sudo apt-get update
Step 4: Installing Jenkins
Now, let’s install Jenkins. Use the following commands:

$$ wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
$$ sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
$$ sudo apt-get update
$$ sudo apt-get install jenkins
To check the Jenkins version, use the following command:


## If the above steps won't help then follow this link steps
* https://pkg.jenkins.io/debian-stable/
* Jenkins Debian Packages
* 
* This is the Debian package repository of Jenkins to automate installation and upgrade. To use this repository, first add the key to your system (for the Weekly Release Line):

    
 * $$ sudo wget -O /usr/share/keyrings/jenkins-keyring.asc  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
  
* Then add a Jenkins apt repository entry:
    
* $$  echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]"     https://pkg.jenkins.io/debian-stable binary/ | sudo tee     /etc/apt/sources.list.d/jenkins.list > /dev/null
  
* Update your local package index, then finally install Jenkins:

   
* $$ sudo apt-get update
* $$ sudo apt-get install fontconfig openjdk-11-jre
* $$ sudo apt-get install jenkins

## Enabling or starting of jenkins

* $$ jenkins --version
* Step 5: Enable and Start Jenkins
* Now, let’s enable Jenkins to start on boot and start the service:

* $$ sudo systemctl enable jenkins
* $$ sudo systemctl start jenkins
* $$ sudo systemctl start jenkins   (To Check Whether Jenkins is running or not)

* Once the Jenkins is active and running. You copy the Public IP Address provided in your EC2 Instance.
* And since by default Jenkins runs in 8080 Port. so browse this way => http://3.111.47.192:8080
* But if somewhow the port won't opens, then you need to do some settings in security groups and enable this port (Inbound Port)
* Just click on Security Group Launch wizard, in inbound rules, do edit, and then add TCP, add PORT 8080, and then 0/0000 only then save.
* video step you can see in this Youtube link : https://www.youtube.com/watch?v=lRpS2CovMrs&t=623s&ab_channel=DSwithBappy
* Once the setup is done. You can re-open the jenkins port on 8080, and it will work fine and jenkins dashboard opens up. => http://3.111.47.192:8080

  
## Getting Started with Jenkins
* Once you are able to open the Jenkins in browser.
* You will get prompt for password.
* copy that and do this command in EC2 CLI
* ubuntu@ip-172-31-1-121:~$ sudo cat /var/lib/jenkins/secrets/initialAdminPassword
* 4f84e9013d0c41e4988ae2815179f667 (You will get Password like this)
* Use that password and login and you will get logged in.
* After login you can install suggested plugins options.





