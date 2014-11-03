---
layout: post
title: Launching Your Server
date:   2014-10-29 12:38:28
position: 20
categories: walkthrough
summary: A configuration guide for provisioning your server in the cloud. This guide will explain the configuration options you can provide and detail the steps rapidcloud.io will take on your behalf to get your instance ready.
---
Before rapidcloud.io can work with your cloud provider you must provide your cloud access keys. Follow these instructions to grant rapidcloud.io access to your cloud account if you haven't done so already. 

When provisioning your instance, you will be prompted to provide some key details

![Server Configuration](/assets/server_add_select_cloud.png)

1. Cloud - Which cloud do you want to use (if you have only connected one cloud then rapidcloud will autoselect it for you)

![Server Configuration](/assets/server_add.png)

1. Name - What is the name of the server
1. Instance Size - This represents the processing power, memory and storage available for your instance. These selections are based directly on the cloud you are using
1. Region - Where should the instance be provisioned. This is a geographic region and should be something you consider carefully, ideally you want to locate the region either closest to your customers or if this is a backup location seperate from your other instances
1. Database - Yes/No - If you select Yes, MySQL will be installed and configured for you. As of now there is no way to add MySQL later, it must be installed as part of the initial setup
1. Database Name (optional) - You can name the default database, if you don't rapidcloud will name it based on your server name
1. Project type - You must select the type of application this server will be configured for. If its a Tomcat application the server will have tomcat setup and installed. If its a Play application, the server will be configured appropriately. This cannot be changed later so make sure you know the type of project. If you are unsure, Tomcat is the safest bet, most applications offer support for Maven and allow you to package thems up as .war files.


Once you have provided all the details, rapidcloud.io will perform the following steps

1. Provision the instance with your cloud provider
1. Wait until the instance is up and able to accept SSH connections
1. Configure the instance based on your provided settings and rapidcloud.io's configuration files (ex: iptables, nginx, mysql, maven, tomcat)
1. Setup accounts. You will have access to an rc-user SSH login which has sudo permissions. If you installed MySQL a seperate rc-user MySQL login will be created.
1. Email you rc-user credentials (You will reieve an email with your instances IP Address, rc-user sudo password and if you installed MySQL you mysql rc-user password)


Once this is complete, you cand deploy your application to the server.