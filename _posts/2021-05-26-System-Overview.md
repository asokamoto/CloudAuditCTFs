---
layout: post
title: "System Overview"
date: 2021-05-28 00:00:05
categories: Levels
comments: false
---

# System Overview 

Hello and welcome to Thunder CTF: cloud security audit and incident response. This is a series of code labs that will walk you through a few basic and a few more advanced cloud security concepts. If you have already played the original Thunder CTF levels, you will have been exposed to most of the concepts contained in these labs. 

The difference between those labs and these is that these labs are a reverse CTF. Most CTF exercises have you seek out the exploit or play what is referred to as the ‘red team’. In our exercises, the exploit has been automated along with the deployment of the environment and you play the defender or the blue team.

Your job will be to study the system and iteratively investigate logs and system details to pick up the paper trail left behind from the exploit. Each level of the codelab sets you up for the next and you follow the fictional hacker in the reverse steps of the exploit, giving you a good idea of how the privileges were escalated. That said, it will be helpful to have an idea of the system resources before you start playing. We have created a diagram with all the components here:

![System Image](ServiceAccounts33.png)

It seems like a lot at first but it actually isn’t too bad. Spending some time familiarizing yourself with the google cloud console will also be beneficial if you need. If you aren’t familiar with IAM or service accounts, [check out the basics from google](https://cloud.google.com/iam). You should have at least a primitive understanding of what service accounts are and how roles are used to limit their access. In cloud environments, a hacker’s goal is usually to move between these service accounts to increase their privileges within the project.

The system we have set up has some resources that a social media company, like twitter, could have. There is a database to store users and their information (like statuses) and a compute engine (runs a flask app) to interact with that data. There is another endpoint in a cloud function for only developers to remove users. Last, there is a bucket used by developers to store the source code of the compute instance that powers the core API. That should be plenty to get started!



