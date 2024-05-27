# Devops Training

## CLASS 6 RECORDING AND LEARNING
* Upto Class 5 and setup of jenkins, job and EC2 check readme.md file
##### JENKINS SECURITY
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
