---
title: "Setting up Domain Name with AWS"
date: 2019-06-03T10:46:53-04:00
draft: true
---

This article will go over how to setup your own domain name and point it to content
either in a AWS S3 bucket or an EC2 instance. We will also secure the connection by
having AWS Cloudfront serve SSL certificates for us.

# Route 53

Route 53 is AWS's domain name service. Domains purchased here can be a bit more
expensive than those bought else where but it has the added benefit of being easier
to setup with other AWS services. A simple `.com` or `.net` will only run you around
twelve dollars a year

###### The Dashboard

In the below picture you'll see the opening screen of the Route 53 page. There's a
lot to take in but the main thing we will focus on is the "Register Domain" part.

!['Route 53 Dashboard'](/img/route53dashboard.png)

In the text box, enter the domain name you and then select whether you want a `.com`
or `.net` or some other suffix from the drop down menu next to the text box. If your
domain name isn't available it will let you know. So play around with that until you
get a domain name you want and add it to the cart.

Next it will ask you to enter in the contact infomartion for the registrant so fill that
out and hit continue. I also Enable Pirvacy protection as well. The next page will ask
if you want to automatically renew your domain. I always click Enable because
I'm forgetful but you don't have to. Then check the box that you've read the terms
and conditions and click "Complete Purchase" and you will have your very own
domain name! Exciting isn't it?

# Setting up Content

But what good is a domain name if you don't have any content to show on it? In this
next we'll instruct our domain name to point to where our webpage is depending on
where you are hosting it

1. S3 Bucket

The most common, and cheapest route, is to host your website in an S3 bucket.
This is especially useful if your website is a static website instead of a
dynamic site. I'll go through the quick steps to get a S3 bucket configured
for web hosting if you don't already have one set up.

2. EC2 Instances

# Cloufront and SSL certificates


