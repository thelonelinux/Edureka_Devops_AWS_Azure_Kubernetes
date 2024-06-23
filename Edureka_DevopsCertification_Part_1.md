# Edureka_Devops_AWS_Cloud
Learning about DevOps, mostly in Amazon AWS in the cloud

## Steps to get started
#### 1. Get an AWS free or Paid Account. For a Free or Paid Account You can check any YouTube videos, there it is explained.
#### 2. Once the account is created. You can start with the AWS Instance Creation.
   * An instance is created on the Cloud, You can choose any OS, etc, and create an EC2 Instance.
   * Steps you can check in Youtube : https://www.youtube.com/watch?v=EXs775-J5zE&ab_channel=GauravSharma
   * Also you can add Shell Script that you want to run automatically when the EC2 Instance is created.
   * for that when creating the instance, goto Advance Details, there you goto User Data attribute. There you can add whatever shell script you want to run.
   * So from here only you can install java and jenkins and start the jenkins. So let's see if it works
      * sudo wget -O /usr/share/keyrings/jenkins-keyring.asc  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
      * echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]"     https://pkg.jenkins.io/debian-stable binary/ | sudo tee     /etc/apt/sources.list.d/jenkins.list  /dev/null
      * sudo apt-get update
      * sudo apt-get install fontconfig openjdk-11-jre (Here -Y Intervention was required)
      * java --version
      * sudo apt-get install jenkins  (Here -Y input was required)
      * jenkins --version
      * sudo systemctl enable jenkins
      * sudo systemctl start jenkins
      * sudo systemctl status jenkins
   * Looks like Jenkins didn't got installed. so better write manually. check later how userdata is used to run scripts.
#### 3. Once the instance is created, connect that instance and open AWS CLI. It is usually like Ubuntu Terminal only if you have chosen Ubuntu as the OS when creating the instance. 
#### 4. Now we will install Jenkins, Jenkins are used to create PIPELINE(Sub-Jobs) for CI/CD. Jenkins is a third party for AWS, it is not pre-installed there. for that, you need to type some below commands. However, AWS has its own Jenkins-like features called, CodeCommit, CodeBuild, and CodeDeploy.
#### 5. The code commit is AWS GitHub like Bitbucket for Atlassian. But let's do Jenkins for now. As they are all paid service.
#### 6. Jenkins is free, but you have to use GitHub to get the latest code for deployment and build jobs. However, CodeCommit CodeBuild and CodeDeploy are paid services of AWS and we don't need GitHub or Jenkins if we have access to these services.
#### 7. CodeBuild, CodeCommit, and CodeDeploy services are accessible for free or paid only if you log in as an AMI user, instead of a root user, when logging into AWS.

----------------------------------------------
<br><br/>

## Installing Jenkins in Amazon EC2 Instance in Ubuntu Image.
* https://medium.com/@shahid199578/installing-jenkins-on-an-ec2-machine-d2e741a07785

* Step 1: Create an EC2 Instance
    * create and connect to an EC2 instance. If you’re not familiar with how to create and connect to an EC2 instance,
    * You can refer to “How to Create and Connect to an EC2 Instance,” for detailed step-by-step instructions.
    * Once you have your EC2 instance ready, you can continue with the installation of Jenkins.

* Step 2: Install Java (java 11 required for jenkins)
    * Jenkins is built on Java, so we need to install it first. Open a terminal and run the following command:

* Step 3: Installing Jenkins after java 11. check the following commands
* https://pkg.jenkins.io/debian-stable/ (This is website where you can find commands)
  
* Jenkins Debian Packages  
* This is the Debian package repository of Jenkins to automate installation and upgrade. To use this repository, first add the key to your system (for the Weekly Release Line):
    * $$ sudo wget -O /usr/share/keyrings/jenkins-keyring.asc  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
  
* Then add a Jenkins apt repository entry:
    * $$  echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]"     https://pkg.jenkins.io/debian-stable binary/ | sudo tee     /etc/apt/sources.list.d/jenkins.list  /dev/null
  
* Update your local package index, then finally install Jenkins:
    * $$ sudo apt-get update
    * $$ sudo apt-get install fontconfig openjdk-11-jre
    * $$ java --version
    * $$ sudo apt-get install jenkins

* Step 4 : Enabling or starting of jenkins
    * $$ jenkins --version
    * $$ sudo systemctl enable jenkins
    * $$ sudo systemctl start jenkins
    * $$ sudo systemctl status jenkins   (To Check Whether Jenkins is running or not)

* Once the Jenkins is active and running. You copy the Public IP Address provided in your EC2 Instance.
* And since by default Jenkins runs in 8080 Port. so browse this way => http://3.111.47.192:8080
* But if somewhow the port won't opens, then you need to do some settings in security groups and enable this port (Inbound Port)
* Just follow below steps
    *  click on Security Group Launch wizard, (Security Menu) you will find that in dashboard in your selected  ec2 instance only, where all details are specified.
    *  Go to inbound rules, do edit, and then add TCP (Custom TCP), add PORT 8080, and then 0/0000 only then save.
    *  Once the setup is done. You can re-open the jenkins port on 8080 in port range, anywhere and other fill 0/000 and then click save rules.
    *  Now our port 8080 is setup and now our jenkins will work fine and jenkins dashboard opens up. => http://3.111.47.192:8080
* video step you can see in this Youtube link : https://www.youtube.com/watch?v=lRpS2CovMrs&t=623s&ab_channel=DSwithBappy


  
## Getting Started with Jenkins
* Once you are able to open the Jenkins in browser.
* You will get prompt for password.
* copy that and do this command in EC2 CLI
* ubuntu@ip-172-31-1-121:~$ sudo cat /var/lib/jenkins/secrets/initialAdminPassword
* 4f84e9013d0c41e4988ae2815179f667 (You will get Password like this)
* Use that password and login and you will get logged in.
* After login you can install suggested plugins options. hERE ONLY GIT IS ALSO GOT INSTALLED. CHOSE SUGGESTED PLUGINS
* After that you create username and password, and then save and continue and then start with jenkins. hence done.
* So this is how you set up jenkins in AWS instance.

## Jenkins as Continous Integration Tool
* This tool has capability to create Job used for Continous Integration. Jobs with some rules and components.
* Example, Jenkins communicate with code and do compilation, do build and do testcases testing etc.
* Jobs like  (Steps of SDLC) :   ( 1. Compile  =>   2. Build  =>  3. Testing  =>  ..    => Package Prepared )  after the package is prepared in CI, then comes CD (Continous deployment)
* So our goals are like to create [1. Compile => 2. Code Review => 3. Unit Test => 4. metric Test => 5. package and then finally 6. Deploy]
* In Maven Related Project : pom.xml file will contain details like which all job is required, if in case devops team is not sure of dependencies and compile tool and testcases.
* Cobertura dependency is used for Unit Teting.
### Creating Jobs in Jenkins (JOBS AND THEIR GOALS ARE DEFINED IN POM.XML FILE ONLY. THIS IS FOR JAVA. FOR OTHER LIKE IN DOTNET WE WILL HAVE SOME OTHER FILE OR WE HAVE TO DISCUSS WITH DEVELOPER WHAT JOB AND GOAL TO USE)
* Can follow below youtube for quick steps
   * https://www.youtube.com/watch?v=8RIFmoWPbhQ&ab_channel=CodersPlace
##### Let's create Compile job for our project AddressBook
* Step 1 : Goto Jenkins, click on left menus (+) icon for new job
* Step 2 : Name your job as addressbookCompile, select FreeStyle project and submit.
* Step 3 : Put this project in git as repository url : https://github.com/htshshrm2/MyAddressbook
   * You should better use this link : https://github.com/htshshrm2/MyAddressbook.git
   * This link you will get when you do clone link for that project. We don't need credentials here as it is public repo.
* Step 4 : Keep branch by default master only : */master
* Also install git in your Ec2 instance. Else it will give error for git when you put url. Also they are usually installed
* Webhook you can update in your github repo from setting, this will make sure that whenever code changes happens, code will be automatically synced in jenkins as well.
* Step 5 For Java Project you have to install maven, you can find that in Jenkins only when creating the build job.
   * Devops can use any programming language and then you can install tools accordingly like for java we need maven to build and for .net nuget tools etc.
      * Tool installation option is in Jenkins,in Manage Jenkins,goto Tools, there you can check and install.
      * Just select maven and also select version you required and then save it.
      * Now goto job configuration setting in prebuild (BuildStep) chose top level maven target and select maven so that it will know that maven in required for this.
      * After this also add goal as "compile".
      * Please select goals as one of this only, and they should be in same case as mentioned below else it will give error
      * Available lifecycle phases are: pre-clean, clean, post-clean, validate, initialize, generate-sources, process-sources, generate-resources, process-resources, compile, process-classes,
      *  generate-test-sources, process-test-sources, generate-test-resources, process-test-resources, test-compile, process-test-classes, test, prepare-package, package,
      *  pre-integration-test, integration-test, post-integration-test, verify, install, deploy, pre-site, site, post-site, site-deploy
* Now if you build the project, you can see in console that maven is getting installed in jenkins node.
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
##### AddressbookCodeReview (Job)
* In Jenkins, click on (+) New Item, name the job as "addressbookCodeReview" and then select "FreeStyleProject" as freeStyleProject is the generic one.
* FreeStyle project will give you all the options in configuration.
* List of all configuration :
* 1. Description : Just add the job description (Any random text) (This job is for code review)
  2. Multiselectors (Discard old build => will help to keep code clean). (Git => helps to select git repo). (Parameterized => Just a feature if your project needs parameter to run). (Throttle build => Prioritize the jobs). (Execute concurrent builds => so it will build concurrently. other users also can push the changes and build)
* 3. Git, we know. Here also again add that same repo for which you are doing code review.
* 4. Build Triggers : Multiple Selection (1. Trigger build remotely: This means you can do build via script or use webhooks. then you can do that here) (2. Build after other job is built : So this is dependency on other jobs. like in pipeline or if some other projects jobs). (3. Build Periodically : If you want to build after every 15 mins etc. ). (4. Git Hook : like webhoook). (5. Poll : means based on criteria. like when any code changes then only build). So this are all the options to do build based on different criterias etc.
* So in Build Triggers : Select Build after other build and inner select build only when the build is stable. As in this way when we run the compile job then after that codeReview of addressbook job will be also triggered in sequence in this pipeline. So in projects to watch add your previous compile job ("addressbookCompile").
* In build steps in top-level maven target : (Select mymaven only which you use in compile job) Now in maven also there is an option to define goal. you can chose (pmd:pmd) plugins. This plugin tool will be usually define in the pom.xm. file to use this tool. If not written then we may not have to use. So since right now its written so we are using this plugin tool. This will create a  side report. Such more jobs role are there for maven. you can check in google.
* So now build the addressbookCompile job only, then you will see once the addressbookCompile job is successfully executed, then addressbookCodeReview will also get executed.

##### addressbookUnittest (Job)
* Same steps as above.
*  git add as url
*  goal describe as "test" in maven goal in invoke top level maven targed,
*  dependency on code review give so that it will run once above is run like in pipeline.
* here in build trigger after "addressbookCodeReview" . So add that.

##### addressbookMetrictest (Job)
* Same steps as above.
* here goal in maven target : Add "cobertura:cobertura -Dcobertura.report.format=xml"
*  here in build trigger after "addressbookUnittest" .So add that.

##### addressbookPackage (Jod)
* Same as above.
* build trigger after "addressbookMetrictest"
* goal in maven add as : "package"

#### Now once all this jobs are created, You can start build of addressbookCompile job, You will see other jobs will also run in sequence.
* Also once you run the build might failed at addressbookMetrictest. as it also needs JDK 8 to run.  But we have JDK 11  in our instance installed when we installed jenkins.
* So now we need to use JDK 8.
* So to install JDK 8 in Jekins. Goto Manage Jenkins, Goto Tools, JDK Installations, Add JDK name as "jdk8" In the JAVA_HOME first we need to install JDK in backend in EC2 Instance
* So goto EC2 Terminal and run command
* $$ sudo apt-get install fontconfig openjdk-8-jre   (Since this command didnot showed java 8 on doing java --version, it was 11  only it showed)
* $$ sudo apt install openjdk-8-jdk  (so running this command to  get jdk 8) (Was still showing java 11)
* $$ sudo update-alternatives --config java (to check wihch all java versions are there in your system and at what path they are present)
* root@ip-172-31-41-107:~# sudo update-alternatives --config java
* There are 2 choices for the alternative java (providing /usr/bin/java).

 *  Selection    Path                                            Priority   Status
* ------------------------------------------------------------
* * 0            /usr/lib/jvm/java-11-openjdk-amd64/bin/java      1111      auto mode (Here star means this is default)
*  1            /usr/lib/jvm/java-11-openjdk-amd64/bin/java      1111      manual mode
*  2            /usr/lib/jvm/java-8-openjdk-amd64/jre/bin/java   1081      manual mode

*  so from here you can chose path "/usr/lib/jvm/java-8-openjdk-amd64" and put in that JAVA_HOME in addressbookMetrictest and run the whole build again.
*  Now once this is added, save it
*  Now go in addressbookMetricTest and define  there this JDK
*  Goto Build Steps, Advance, In JVM Option add "jdk8" which you added in the tools. same name only add and then save.
*  BUT still it got failed with main file load error. So now this time We will make java 2 in above list as default one. that is java 8 as default preesnt in 2nd position in the list.
*  So for that run the command
*  $$ sudo update-alternatives --config java
*  After you run this command you will get invoke to chose the default jdk
* $$ => Press <enter> to keep the current choice[*], or type selection number: 2
* $$ => update-alternatives: using /usr/lib/jvm/java-8-openjdk-amd64/jre/bin/java to provide /usr/bin/java (java) in manual mode
* root@ip-172-31-41-107:~# sudo update-alternatives --config java
* There are 2 choices for the alternative java (providing /usr/bin/java).

*  Selection    Path                                            Priority   Status
* ------------------------------------------------------------
*  0            /usr/lib/jvm/java-11-openjdk-amd64/bin/java      1111      auto mode
*  1            /usr/lib/jvm/java-11-openjdk-amd64/bin/java      1111      manual mode
** 2            /usr/lib/jvm/java-8-openjdk-amd64/jre/bin/java   1081      manual mode (Here star means this is default)

* Now since we have made java jdk 8 as our default. so we don't have to any more add jdk tool and hence now we can remove jdk8 in Build Steps from addressbookMetrictest job
* Now after removing it and re-run the jobs. This time everything will work fine.
* 

### Once the build is successful (What to check)
* You can see in addressbookPackage in workspace, inside the target folder, We have got war file created.
* Also in addressbookMetrictest. you can see in workspace, there is cobertura report is generated.
* In build you can see it will say that cobertura report is generated and all that stuffs.

### So now about Plugins In Jenkins
* So here in each job, you are not getting any job status, report status to report our pipeline.
* So for that we can have plugins. so to add more functionalities in jenkins by adding more plugins.
* so goto jenkins manager, goto plugins, and there search for plugins you required in Available Plungins. If it's not available means it's already installed.
* Also if you want to get report within a job then there is post build attributes in each job. there you can attach this plugins and provide file targets of htat report.
* You can add path of this plugins there. in post build report. like for cobertura and junit. Path you can find when you go in workspace of each job where you are adding that plugins.
* So let's add plugins in post build attribute for addressbookUnittest and Junit plugins in it. First check in plugins in manage jenkins if we have this plugins installed.
* So if it is installed. goto addressbookUnittest, goto post build attribute, there select, "publish Junit report"
* Now select the path of the file, where the report will be generated.
* so to check this path. goto workspace, there go in the target folder, sure-fire reports folder. there you can see 3 xml file starting wiht TEST, so they are our target files paths.
* so now we already have those test results present there but they are not visible and shown properly.
* With Jenkins plugins, it helps us to read those Jenkins plugins alongside our pipeline build
* so in our target path add "target/surefire-reports/*.xml"  (So this * will pick all xml file present in the surefire-reports folder) 
* so now save and build that job. you can see test will show directly in the workspace. (to crosscheck whether this file folder are there you can go in the workspace and check)
* So now once the build is done. click on #Number (Build #), there you can see it will show you test results. so now you can see the total results and their status there.
* So now you can see the output files.
* SO NOW FOR COVERAGE ANALYSIS: We have covertura plugins.
* so go to manage plugins and install cobertura. This will help to read those output files created in MetricTest job.
* So go in the metricTest job, configure this plugin in post build options, select Publish Cobertura coverage report.
* And provide the path of the coverage report  : "**/target/site/cobertura/coverage.xml" (so check where this xml file is located with cobertura)as this will be our path required.
* so put this path, and then build the metrictest job.
* Once the build is done click on build (#),You can see there it will give you coverage report. so click on coverage report. You will see whole report there.
* SO NOW THERE IS ANOTHER PLUGIN : BUILD PIPELINE
* So install this plugin
* So now create a new view : This is plus icon (+) on the right side of ALL. so click on it
* Name it as : Addressbook
* Select radio button : build pipeline view and then create it
* this will help us to see the pipeline in good format
* Here chose addressbookCompile as "initial Job" as this is our first job, and then click on OK
* So now you can see the same pipeline in the form of cards.
* So this is good to see how code progress, this is only for demonstration. So run it and you can see. So that's all it.
* QnAs time.

#### SCM Polling
* This you can add in addressbookCompile job.
* for three minutes in configuration add. click on Poll SCM Options in configure and in box add this "H/3****". 
* this will check your git code changes after every 3 mins. And if there is any code changes, it will build all over again.

## Code Deployment
* So now the jar/war file is created in the Job addressbookPackage. Now we need to deploy it.
* So we need to create another job i.e. deploy job after package job.
* Also to deploy that project package we need an environment to deploy that package. (Dev / QA / UAT / Prod) Environment.

* -----------  END OF CLASS 5 RECORDING ----------------------


