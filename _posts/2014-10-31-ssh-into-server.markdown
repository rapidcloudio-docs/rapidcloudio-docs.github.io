---
layout: post
title: SSH Access
date:   2014-10-31 12:38:28
position: 10
categories: walkthrough
---
Any of your servers can be accessed via SSH once you upload your public key. 

1. Generate an ssh key using the following command: ssh-keygen
1. Follow the steps to setup a key

{% highlight bash %}
$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/home/fred/.ssh/id_rsa): test_rsa
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in test_rsa.
Your public key has been saved in test_rsa.pub.
The key fingerprint is:
c6:11:e8:d6:fb:18:fc:78:7c:bd:6d:2c:2e:47:d3:2d fred@FredLenovo
The key's randomart image is:
+--[ RSA 2048]----+
|       ..        |
|      .  .       |
|     . ..        |
|      o...       |
|     . .S.     ..|
|       .+     E o|
|         B   o + |
|        o = o +.o|
|         . . +o+.|
+-----------------+

$ ls
test_rsa  test_rsa.pub
{% endhighlight %}


Once its complete, copy the contents of the public key file(by default its located here: ~/.ssh/id_rsa.pub) and upload it to rapidcloud. 

![Upload SSH Key](/assets/upload_ssh_key.png)

1. Name - A friendly name so you remember which key this is
1. Public Key - The contents of your public ssh key

After you click the Add Public Key button, rapidcloud will publish your key to the server, this may take a few minutes. 

Once your key has been successfully published, you'll be able to log into your server with the following ssh command:
	
{% highlight bash %}
$ssh -i (path to private key file) rc-user@(server ip address)
{% endhighlight %}

Using our server example: 
{% highlight bash %}
ssh -i test_rsa rc-user@107.170.140.205
{% endhighlight %}

In order to gain root access you'll be required to provide the sudo password you were emailed when your server was setup.
{% highlight bash %}
$ sudo su
{% endhighlight %}


If you lost the email, you can reset your rc-user password from the password page.

![Password Reset Page](/assets/password.png)

