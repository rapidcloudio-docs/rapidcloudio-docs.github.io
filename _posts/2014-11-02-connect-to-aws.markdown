---
layout: post
title: Connecting to AWS
date:   2014-11-02 12:38:28
position: 15
categories: walkthrough
summary: Step by step guide for connecting your rapidcloud.io account to your AWS account.
---
In order for rapidcloud.io to provision instances for you at Amazon Web Services (AWS), you need to generate an access key for us to use. In this guide we'll walk you through the process of generating an IAM access key step by step.

Start by navigating to the IAM page on AWS. You can access it from Services > Deployment & Management > IAM on the AWS navigation bar.
![AWS Navigation](/assets/get_key_aws_nav.png)

Once on the IAM page, create a new user, and specify a username you'll recognize (ex: rc-service-user )
![AWS Navigation](/assets/get_key_aws_step1.png)

After you create the user, save the credentials, you'll need to provide these to rapidcloud.io later.
![AWS Get Credentials](/assets/get_key_aws_step2.png)

Open up the user detail page, and select Attach User Policy
![AWS View User](/assets/get_key_aws_step3.png)

For policy, select Custom Policy 
![Select Policy Template](/assets/get_key_aws_step4.png)

Provide the rapidcloud.io policy document
{% highlight javascript %}
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Action": "ec2:*",
      "Effect": "Allow",
      "Resource": "*"
    }
  ]
}
{% endhighlight %}

![Set Permissions](/assets/get_key_aws_step5.png)

1. Login to your rapidcloud.io account
1. Navigate to the [cloud management page](https://rapidcloud.io/my/cloud)
1. On the AWS Panel select Connect
1. Select AWS from the drop down
1. Enter your Access Key ID and Secret Access Key you copied after you created the IAM user

![Provide Keys to Rapidcloud.io](/assets/get_key_aws_step6.png)

After saving you are now ready to provision servers at AWS.