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
* After that you create username and password, and then save and continue and then start with jenkins. hence done.
* So this is how you set up jenkins in AWS instance.

## Jenkins as Continous Integration Tool
* This tool has capability to create Job used for Continous Integration. Jobs with some rules and components.
* Example, Jenkins communicate with code and do compilation, do build and do testcases testing etc.
* Jobs like  (Steps of SDLC) :   ( 1. Compile  =>   2. Build  =>  3. Testing  =>  ..    => Package Prepared )  after the package is prepared in CI, then comes CD (Continous deployment)
* So our goals are like to create [1. Compile => 2. Code Review => 3. Unit Test => 4. metric Test => 5. package and then finally 6. Deploy]
* In Maven Related Project : pom.xml file will contain details like which all job is required, if in case devops team is not sure of dependencies and compile tool and testcases.
* Cobertura dependency is used for Unit Teting.
### Creating Jobs in Jenkins
* https://www.youtube.com/watch?v=8RIFmoWPbhQ&ab_channel=CodersPlace
* Step 1 : Goto Jenkins, click on left menus (+) icon for new job
* Step 2 : Name your job as AddressBookCompile, select FreeStyle project and submit
* Step 3 : Put this project in git as repository url : https://github.com/htshshrm2/MyAddressbook (https://github.com/htshshrm2/MyAddressbook.git) This you will get when you do clone link for that project. We don't need credentials here as it is public repo.
* Step 4 : Keep branch by default master only : */master
* Also install git in your Ec2 instance. Else it will give error for git when you put url. Also they are uusally installed
* Webhook you can update in your github repo from setting, this will make sure that whenever code changes happens, code will be automatically synced in jenkins as well.
* For Java Project you have to install maven, you can find that in Jenkins only when creating the build job.
* Devops can use any programming language and then you can install tools accordingly like for java we need maven to build and for .net nuget tools etc.
* Tool installation option is in Jenkins,in Manage Jenkins,goto Tools, there you can check and install.
* Just select maven and also select version you required and then save it.
* Now goto job configuration setting in prebuild (BuildStep) chose top level maven target and select maven so that it will know that maven in required for this.
* After this also add goal as "compile".
* Please select goals as one of this only, and they should be in same case as mentioned below else it will give error
* Available lifecycle phases are: pre-clean, clean, post-clean, validate, initialize, generate-sources, process-sources, generate-resources, process-resources, compile, process-classes, generate-test-sources, process-test-sources, generate-test-resources, process-test-resources, test-compile, process-test-classes, test, prepare-package, package, pre-integration-test, integration-test, post-integration-test, verify, install, deploy, pre-site, site, post-site, site-deploy
* Now once you build the project, you can see in console that maven is getting installed in jenkins node.
* Right now JDK is not required in the tools. So leave it for now. Else you can chose and add java home for selected jdk, in automatica installer only latest will get added.
* Once the build is done. they (maven) will be automatically get installed once the build is done. You can see in console.
* Once the build is successful, the job gets created successfull.
* Code compile succesfull happens you can check all the files you added from github in workspace menu.
* You can also check in EC2 level CLI. just do $$ cd /var/lib/jenkins/workspace  and then $$ ls (Here inside this directory, you can see that addressbookCompile job folder gets created)
* ubuntu@ip-172-31-1-121:/var/lib/jenkins/workspace$ ls
* addressbook  addressbookCompile
* For testCases job Junit etc. you need to add that also in the code in github. In above addressbook url test code are also added.
* 
* -----------      THIS IS ALL UPTO CLASS 4 RECORDING IN DEVOPS EDUREKA TRAINING    --------
* 

### CLASS 5 RECORDINGS (WE WILL BE CREATING MORE JOBS IN JENKINS LIKE, COMPILE, CODE REVIEW,  TEST, METRIC TEST, PACKAGE AND THEN DEPLOY)
* In Jenkins, click on (+) New Item, name the job as "addressbookCodeReview" and then select "FreeStyleProject" as freeStyleProject is the generic one.
* FreeStyle project will give you all the options in configuration.
* List of all configuration :
* 1. Description : Just add the job description (Any random text) (This job is for code review)
  2. Multiselectors (Discard old build => will help to keep code clean). (Git => helps to select git repo). (Parameterized => Just a feature if your project needs parameter to run). (Throttle build => Prioritize the jobs). (Execute concurrent builds => so it will build concurrently. other users also can push the changes and build)
* 3. Git, we know. Here also again add that same repo for which you are doing code review.
* 4. Build Triggers : Multiple Selection (1. Trigger build remotely: This means you can do build via script or use webhooks. then you can do that here) (2. Build after other job is built : So this is dependency on other jobs. like in pipeline or if some other projects jobs). (3. Build Periodically : If you want to build after every 15 mins etc. ). (4. Git Hook : like webhoook). (5. Poll : means based on criteria. like when any code changes then only build). So this are all the options to do build based on different criterias etc.
* So in Build Triggers : Select Build after other build and inner select build only when the build is stable. As in this way when we run the compile job then after that codeReview of addressbook job will be also triggered in sequence in this pipeline. So in projects to watch add your previous compile job ("addressbookCompile").
* In build steps in top-level maven target : Now in maven also there is an option to define goal. you can chose (pmd:pmd) plugins. This will create a  side report. Such more jobs role are there for maven. you can check in google.
* So now build the addressbookCompile job only, then you will see once the addressbookCompile job is successfully executed, then addressbookCodeReview will also get executed.



