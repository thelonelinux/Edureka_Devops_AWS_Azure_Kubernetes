# Devops Training
* Don't open Freetier AWS until may end. for threshold is reached and will cost you if you use instance etc.
* In github also we can create jobs like jenkins, call github actions. You can look about it on youtube internet.
## CLASS 6 RECORDING AND LEARNING
* Upto Class 5 and setup of jenkins, job and EC2 check readme.md file
#### JENKINS SECURITY
* Here we will learn about security and stuffs in Jenkins
* For Security in Jenkins you can check in by goto Manage Jenkins, there you will find security options
* Click on it. There you will see different options for Authentication and Authorization, about who can access that job pipeline and who can do what access like thing.
* We can chose which users to given what access.
* So to do that, you can create users in Manage Jenkins, Users.
* Once you create multiple Users, go to Authorization, and there you can see Matrix bases Authorization, which means you can give certain type of access to certain users.
* Over there Click on Add User and just give him whatever rights you want for them.
* So when you login to jenkins via those username and password, then you might be able to get only whatever rights you have provided them in Authorizatrion Matrix based.
* So this is one way to secure your jenkins
* Authorziation : project based matrix - here we can also give users access to certain projects/ pipeline. so this is also one of security options you have in jenkins

##### JENKINS NOTIFICATION (EMAIL NOTIFICATION)
* In Jenkins we use plugin Email Extension Plugin to enable email notificiation
* You can see in youtube or in ppt how to setup the attributes. like postBuild email etc.

##### MASTER SLAVE NODE IN JENKINS
*


##### PIPELINE AS A CODE
* In your addressbook code in github, you can see there is "jenkinsfile"
* This file will help us to do pipeline as a code.
* So instead of developer being dependent on Devops team to create a job for your project. Dev guy can also create this job written in this "jenkinsfile" along with the project.
* This jenkinsfile contains code functionality related to your job. So we can push this code and create jobs in jenkins.
* Also this file should be named as "Jenkinsfile" only, then only it will able to identify.
* So this time let's create  a job, name it as "pipelineascode", chose  pipeline instead of freestyle and create it
* Paste the URL, by default it will chose Jenkins file.
* Syntax Generator : Also there you can find how to create syntax (Generate Pipeline syntax) to write code for pipelineasacode for different jobs task features of your job.
* This Jenkinsfile is however written in Groovy Language. But you don't need to learn deep about it,as syntax generator will help.
* Now run it. It will show you the whole build steps and jobs on it's own. (All this job task are taken from Jenkins file)
* So here it's just one job "pipelineascode" and we were able to perform all the task in it. Unlike previously where we created separated jobs.
* TWO types of PIPELINE is there (In terms of approach)
  * 1. Descriptive : (Stages) The one we used that code in jenkinsfile
  * 2. Scripted : (Stages outside node block) Here actions to be performed in specific node is mentioned.

### ANSIBLE (CONFIGURATION MANAGEMENT TOOL) (To be used for deployment and use of many servers like prod, dev, qa and uat)
* Other tool are puppet, chef. Here we will use Ansible
* Ansible Architecture :
    * Ansible Master Node  => Push approach to manage configuration in slave node (Web server, SSH server, etc). Real time changes and synced
    * Ansible Msater Node  => Pull approach (Agent is required to talk with servers (so here we are dependent in agent, so this is not good and not that sync). This is done by Puppet tool
    * So this is the reason Ansible is better than Puppet. As we have push approach in Ansible.
* Configuration Management tools provide an easier approach to manage and configure servers.
* It manages the entire infrastructure
* Here scripting is done in configuration management tool, instead of writing scripts in different servers which will be more complex otherwise.
* Infrastructure as a Code: This is same like Pipeline as a Code in jenkins. Here also we will define scripts manually and store jobs there to do configuration management in ansible server.
* Playbooks: Playbooks are scripts written in ansible. Inside the Playbook you write actions known as Plays.
* Ansible consists (Contains) of 4 items in it's architecture :
  *   1. Inventory (Where you implement the changes) (This contains the list of servers you are managing, It can be also group of servers) ,
  *   2. Modules (Here you find what actions are to be performed) (Predefined codes to perform task, like copy, install etc), 
  *   3. API (To do any cloud related operations) (Like AWS, GCP cloud you want to manage then this will help) and
  *   4. Plugins (To enhance the functionality)
* Next we will see how to install Ansible in server and also do TomCat Server. Agenda for next class.
* QnA
* TerraForm is infrastructure management (like CPU hardware), Ansible is for Configuration management and sometimes Infrastructure. (Sometimes they overlap)
* There is Deploy Goal in Maven, Then why we need Ansible to Deploy -
  * It is because Deploy goal in maven will deploy in Jenkins server only.
  * But here we are talking about PROD, QA, UAT servers also, which are separate from jenkins servers
  * So that's why we need configuration management tool to address all those servers.
*
* --------------------------------  END of CLASS 6 Recording ---------------------------------

### CLASS 7 RECORDING STARTS
* We will learn how to setup Ansible and in-depth Details
##### ANSIBLE (Check in details in video later)
* Install Ansible and then tomCat server in our EC2 CLI and run the servers.
* Also work with documentataion

##### Now In Jenkins also we can install Tom cat server and deploy our package (Check in details in video later)
* So we have to make two job "addressbookTomCatInstall" and "addressbookDeploywar".
* This will run in pipeline after "addressbookPackage".
* Once it is sucessfully deployed, you can open webiste url and can see your web-page.

##### HANDLERS
*

##### ANSIBLE ROLES
*


##### QnA
* 



