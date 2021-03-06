---
layout: post
title: SSH Access
date:   2014-10-31 12:38:28
position: 100
categories: walkthrough
summary: How to gain SSH and sudo access to your server instance.
---
Any of your servers can be accessed via SSH once you upload your public key. 

This guide will demonstrate how to:

1. Generate an SSH key (if you don't already have one)
1. Upload your SSH key
1. SSH onto your server
1. Gain sudo access
1. Reset your sudo password


### Generate an SSH key
From your console (linux, mac or cygwin), run the command <code>ssh-keygen</code>

In this example, I'll create an ssh key in the default folder with no passphrase:

{% highlight bash %}
$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/home/fred/.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/fred/.ssh/id_rsa.
Your public key has been saved in /home/fred/.ssh/id_rsa.pub.
The key fingerprint is:
14:ec:a6:03:9a:52:2e:0c:7a:a9:40:05:be:7b:ee:e2 fred@FredLenovo
The key's randomart image is:
+--[ RSA 2048]----+
| ..    ..        |
|.  .    ..       |
| ..    ..        |
|..o .  .o        |
|=+ + . oS        |
|=.B   o          |
|.* .   .         |
|..o              |
|.Eoo             |
+-----------------+

$ ls ~/.ssh/
bak  id_rsa  id_rsa.pub  known_hosts  known_hosts.old

$
{% endhighlight %}

### Upload your SSH key
Once its complete, copy the contents of the public key file, by default its located here: ~/.ssh/id_rsa.pub and upload it to rapidcloud. 

![Upload SSH Key](/assets/upload_ssh_key.png)

1. Name - A friendly name so you remember which key this is
1. Public Key - The contents of your public ssh key

After you click the Add Public Key button, rapidcloud will publish your key to the server, this may take a few minutes. 

### SSH onto your server
Once your key has been successfully published, you'll be able to log into your server with the following ssh command:
	
{% highlight bash %}
$ssh -i (path to private key file) rc-user@(server ip address)
{% endhighlight %}

Using our server example: 
{% highlight bash %}
ssh -i test_rsa rc-user@107.170.140.205
{% endhighlight %}

### Gain sudo access
In order to gain root access you'll be required to provide the sudo password you were emailed when your server was setup.
{% highlight bash %}
$ sudo su
{% endhighlight %}

### Reset your sudo password
If you lost the email, you can reset your rc-user password from the password page.

![Password Reset Page](/assets/password.png)

