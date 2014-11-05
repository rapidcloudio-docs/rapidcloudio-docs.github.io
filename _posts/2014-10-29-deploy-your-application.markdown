---
layout: post
title: Deploying Your Application
date:   2014-10-29 12:38:28
position: 30
categories: walkthrough
summary: Step by step walkthrough to getting your application installed from GitHub or Bitbucket, built and deployed to your new server. 

---
Once you've finished provisioning a server, you will be able to deploy your Java web application to the instance. This process consists of three steps

1. Clone your GIT repository
1. Configure your deploy settings
1. Run the deploy step

## Clone your GIT repository

To install your GIT repository, you'll need to have connected your rapidcloud.io account to BitBucket and/or Github. At this time rapidcloud.io only supports pulling applications from those two services.

Once you've done that, go your your server's repository page and provide the following details

![Clone GIT Repository](/assets/select_repository.png)

1. Source (GitHub/Bitbucket) - Select which GIT provider is hosting your application code
2. Repository Name - What is the name of your repository. If you don't have one yet, you can fork [our quickstart application]({% post_url 2014-11-03-springboot-quickstart %}).
3. Branch - Which branch do you want to pull from. This can be the master branch or any branch you have defined. 

Once you've finished this step, your repository will be cloned on your server.  

Your repository will be stored in:
<code>/home/rc-build/repository</code>

## Configure your deploy settings
Deployment settings are one of the most complex features of rapidcloud.io. They also depend on which type of project you are deploying. 

### Tomcat Projects
Tomcat projects, use Maven to build and package up your war file. You'll have the following configuration options

![Tomcat Configuration](/assets/tomcat_configuration.png)

1. Autodeploy (Yes/No) - Should rapidcloud.io automatically check for changes in your repository and if it finds them automatically attempt to deploy them. 
1. Build Strategy (Custom/Default) - Default means maven is executed with the command "mvn clean package". If you want to run other commands or change that you can customize it here. However after this command is run, rapidcloud will require that a war file be present in the target/ directory. (Note: Your build command is executed from the /home/rc-build/repository directory)
1. Profiles - Specify which build profile(s) should be used. If you are using our springboot quickstart, then specify the profile webapp
1. Additional Arguments - If you want to pass run time arguments to catalina.sh, provide them here. Note: Whatever is provided in this field will be passed verbatim to catalina.sh
1. Startup time - How much time should your application be given to startup. 
1. Confirmation Url (optional) - After deployment which url should be checked to verify that deployment was successful. This is very useful especially when running parallel deployments.
1. Enable parallel deployment (Yes/No) - If set to no, rapidcloud.io will restart tomcat (8080 instance) with each deployment. If set to yes, rapidcloud.io will alternate deployments between your two tomcat instances (8080 and 8081), waiting for the new instance to start before terminating the old one. This is a good option to minimize downtime.

### Play Projects

![Play Configuration](/assets/play_configuration.png)

1. Autodeploy (Yes/No) - Should rapidcloud.io automatically check for changes in your repository and if it finds them automatically attempt to deploy them. 
1. Build Strategy (Custom/Default) - Default means sbt is exected with the command "sbt clean compile stage -Dsbt.log.noformat=true". If you want to run other commands or change that you can customize it here. However after this command is run, rapidcloud will require that play is packaged for deployment. (Note: Your build command is executed from the /home/rc-build/repository directory)
1. Apply (default) database evolutions - Should Play attempt to apply the forward database evolutions automatically. This is only recommended for development environments.
1. Config Resource - Specify the name of the application conf file you want to use. Play will look for it on the classpath.
1. Logging Resource - Specify the name of the logging conf file you want to use. Play will look for it on the classpath.
1. Additional Arguments - Any additional command line arguments you may want to pass to Play. These are provided verbatim to the Play startup script.
1. Startup time - How much time should your application be given to startup. 
1. Confirmation Url (optional) - After deployment which url should be checked to verify that deployment was successful. This is very useful especially when running parallel deployments.

## Deploying
Click Deploy Now once you are ready to deploy. Your request will be confirmed by a small toast in the bottom right of your screen.
![Deploy Now](/assets/deploy_now.png)




