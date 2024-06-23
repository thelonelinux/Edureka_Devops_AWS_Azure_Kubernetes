# Devops Training
* Don't open Freetier AWS until May end. for threshold is reached and will cost you if you use instance etc.
* In GitHub also we can create jobs like jenkins, call github actions. You can look at it on YouTube internet.
## CLASS 6 RECORDING AND LEARNING
* Upto Class 5 and setup of Jenkins, job, and EC2 check readme.md file
#### JENKINS SECURITY
* Here we will learn about security and kinds of stuff in Jenkins
* For Security in Jenkins you can check in by going to Manage Jenkins, there you will find security options
* Click on it. There you will see different options for Authentication and Authorization, about who can access that job pipeline and who can do what access like thing.
* We can choose which users to give what access.
* So to do that, you can create users in Manage Jenkins, Users.
* Once you create multiple Users, go to Authorization, and there you can see Matrix-based Authorization, which means you can give certain type of access to certain users.
* Over there Click on Add User and just give him whatever rights you want for them.
* So when you log in to jenkins via those username and passwords, then you might be able to get only whatever rights you have provided them in Authorizatrion Matrix based.
* So this is one way to secure your Jenkins
* Authorization: project-based matrix - here we can also give users access to certain projects/ pipeline. so this is also one of security options you have in jenkins

##### JENKINS NOTIFICATION (EMAIL NOTIFICATION)
* In Jenkins we use plugin Email Extension Plugin to enable email notification
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
* --------------------------------  END of Lecture 6  ---------------------------------

## CLASS 7 RECORDING STARTS
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
* --------------------------------  END of Lecture 7  ---------------------------------

## CLASS 8 RECORDING STARTS
##### CONTAINERIZATION  
* Let's explain by a scenario : Example we have developer whose code is working fine in his local machine, and then now he push the code deployment in dev, or prod.
* But sometimes what happens, there is some libraries which is specifically required to run the code, Now operations team deploy it, but it fails. so now this becomes a blame game
* No one will know exactly what happens, this is all because of some version libraries which is required for different environment etc.
* So we came up with solution that "why not we add package, binaries and libraries along with the code"
* Previously we were not doing this as binaries and libraries were installed in operating system.
* So we require OS to install binaries and libraries.
* But with Containerization we don't need that. There is no OS in Container.
* Containerization is the process or the procedure to package the binaries and the libraries along with the code. This together is called Image. We can run this image in multiple env.
* Developers create this Image.
* Containerization System (Tools) : Docker, Rocket, LXI, Crio, etc.
* We will learn Docker.
###### DOCKER
* Docker is a containerization engine and not container itself.
* So in a host machine we install Docker and within docker we create containers.
* Difference between Virtualization (Virtual Machine - Here OS to be installed in host OS to run app) and Containerization (Container - Here it will take Host OS only to run libraries and apps)
* Also in container Host OS (Kernel is required). So we can have Ubuntu type of Application or Windows type for specific container.
* Such things can be more usefule for Microservice architecture which nowadays is going on. So here maintenance is easy with container.
* Docker (Container runtime engine) - CLI is used to maintain container lifecycle
* Docker Architecture
 * 1. Docker Client (Docker CLI or Remote API)
 * 2. Docker Host (Daemon- It's a docker service. Containers images - from docker hub it is cached locally on host)
 * 3. Docker Registry ( Central Repository - Where we store our Images centrally in docker Hub, here we push the image like github and pull if we require some images)
* Container Lifecycle : Created, running , paused, start, restart, stop, terminated etc. you know
* Install docker in EC2 CLI.
* check commands
* Getting started with docker and container
##### DOCKER and Commands and Images and Container and Lifecycle
* check Later
* here in this google drive linke you can fine commands : https://drive.google.com/drive/u/0/folders/1oDgzHUOvWaxrvUxn2ntLnGzDQYi2bCpF

* Container are by default stored in Memory only. Containers are always live.

##### Running Container in foreground and in Detach Mode (Background)
* foreground : it will drop you in container
* Background : it will run in background and you can got in later.

##### DOCKER FILE
* Commands : RUN, FROM, COPY CMD, EXPOSE. to setup the container and image.
* Addressbook was dependent on TomCat Image.
* So we can use that Image only,( or we could have also created new)
* Also get the war file in the container.
* So our command will be like
 * FROM tomcat COPY addressbook.war .... (like this)
* There is sample image in sir's github : https://github.com/htshshrm2/docker-tomcat-tutorial
* So this repo itself is a image. which contains tomcat and war file. Which are added in container.
* So in Docker file you can see there is tihs same command written.
* So clone this repo in EC2 commandline only, and then ls, there you will see the container. So now create the image.
* Do some command to create the image. So now your application is expose to 8080 Port, but not for outside world as it is inside container and not in host.
* So to do that we need port mapping. Do by some command, see in lecture video.

##### DOCKER CREATE IMAGE AND PUBLISH as ADDRESSBOOK JOB
* Add Docker plugins, rest see steps in lecture video only.
* "addressbookBuildImage", "addressbookPushImage", "addressbookDeployContainer".
* This all jobs in jenkins sir will create and show us later. Right now due to some issue the jobs were not running.

##### QnAs
*  --------------------- END of Lecture 8 ----------------------------------------

## CLASS 9 RECORDING STARTS
##### Integration of Docker in Jenkins (In our Pipeline)
* The whole purpose of learning Docker is so that we can integrate this in our Jenkins Pipeline.
* So for that integration we will be creating this 3 jobs in jenkins : "addressbookBuildImage", "addressbookPushImage", "addressbookDeployContainer".
* So we have that Docker file in our github ( https://github.com/htshshrm2/docker-tomcat-tutorial), from there we will create the image and then we will create our container.
* Also, firstly we need to create Docker Host by exposing docker API/Service in our jenkins.
* Also need to expose Docker API to TCP. After this add Docker host to jenkins and then create our jobs, addressbookImage and then addressbookcontainer. Becaues we need image to create a container.
* Steps you can find in google Drive in Docker Jenkins Integration
* We can communicate Jenkins with docker by exposing it to TCP only which is done by docker API.
* You can check if docker service is exposed or not using below command.
* So now go to Jenkins and create the docker cloud in manage Jenkins.
* Dockerfile is there in our addressbook github repo also.
* check videos for more in lecture

##### DOCKER VOLUMES
* check for more in lecture videos only
* Copying data from one host to another.
* Later Kubernetes can be helpful for host managements.
* Remember in tomcat file we have to create roles there.

##### DOCKER COMPOSE FILE

##### DOCKER SWARM
* To create clusters of docker host
* Docker Swarm Nodes  : Manager Node, Leader Node, Worker Nodes
* docker swarm should not be misused like Kubernetes as it too manage multiple docker host.

##### QnAs
* *  --------------------- END of Lecture 9 ----------------------------------------


## CLASS 10 RECORDING STARTS
##### DOCKER SWARM
* Dcoker swarm is an Orchstrator specifically for Docker
* Orchestrator : When there are multiple Docker Host wihch cootains multiple Container. So to take care of each docker host, you have to move from one cli to other docker host cli.
 * Hence to Control all these docker host by single means, we need a Orchestrator. hence for docker we have docker Swarm,
 * We don't need to install anything once docker is there, swarm also gets installed.
 * docker swarm only supports docker 
* However in Kubernetes (which is also a orchestrator tool) we can support multi-container runtime engine.
* So kubernetes is not only limited to Docker. Kubernetes support multiple container engine
* Also, docker swarm is used in areas with smaller container clusters. so mostly we use Kubernetes only.
* so now install docker and docker swarm in EC2 (check video lecture)
* docker commands and swarm commands
* Docker Swarm : Rollback and update done efficiently in Real time online only for different container.
##### NAMESPACES 
* It's a linux feature. Not a container feature
* it is used to keep process isolated, As containers are also kept isolated using this namespace
* When a new container is created, a new namespace for htat container is created.
* In Kubernetes we can decide which container sshould contain which namespace.
* If the two container have same namespace, then they will share the same environment, like the IP address, Processes, memory etc.
* So namespaces is used to isolate process in the system.
##### C-GROUPS
* Similar to namespace, but here we are not isolating the environment, here we are isolating the resources. Example CPU, RAM.
* We can specify CPU and RAM for container as per requirement from the host. so it is giving a capability to setup the limit.
* so how we can do that, see in lecture video for commands. To setup the limits for CPU and RAM.

#### KUBERNETES
* 














