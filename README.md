# Edureka_Devops_AWS_Cloud
Learning about Devops, mostly in Amazon AWS in cloud


# About installing Jenkins in Amazon EC2 Instance in Ubuntu Image.
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

$$ jenkins --version
Step 5: Enable and Start Jenkins
Now, let’s enable Jenkins to start on boot and start the service:

$$ sudo systemctl enable jenkins
$$ sudo systemctl start jenkins


# If above steps won't help then follow this link steps
* https://pkg.jenkins.io/debian-stable/
