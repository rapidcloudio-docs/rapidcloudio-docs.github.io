---
layout: post
title: Quickstart with Springboot
date:   2014-11-03 12:38:28
position: 25
categories: walkthrough quickstart
summary: We created a fast way to get started using a preconfigured scaffolded springboot application. 
---

##Prerequisites
A server provisioned with MySQL and Tomcat 8/Maven. 
![GitHub Screenshot](/assets/quickstart_springboot_pre_req.png)


## Fork the quickstart project
We have a quickstart springboot project available for forking on Github. Just go to [https://github.com/rapidcloudio-docs/rapidcloudio-quickstart-springboot](https://github.com/rapidcloudio-docs/rapidcloudio-quickstart-springboot) and fork the project into your own Github account.
![GitHub Screenshot](/assets/quickstart_springboot_github.png)

Once that's complete you can now deploy the quickstart application to any of your servers configured for Tomcat 8/Maven which have MySQL installed.

## Launching the quickstart
Your next steps are 

1. Clone the forked repository onto your server
1. Configure the build process to use a specific Maven profile
1. Deploy your application

#### Cloning the repository
![GitHub Screenshot](/assets/quickstart_springboot_repository.png)

1. Source: Github
1. Repository Name: rapidcloudio-quickstart-springboot
1. Repository Branch: master

#### Adjust your server configuration
![GitHub Screenshot](/assets/quickstart_springboot_configuration.png)

1. Profiles: webapp

#### Deploy the application
After the repository is cloned and you've set the Maven profile, click the deploy now button. 
![GitHub Screenshot](/assets/quickstart_springboot_deploy.png)

#### View the application
Once the deployment is done go ahead and view the hello world page, by navigating your server to your server's IP address (find it on the left side informational panel or the server's overview page).
![GitHub Screenshot](/assets/quickstart_springboot_hello_world.png)
