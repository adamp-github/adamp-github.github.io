
## 22nd January 2023 - AWS Workmail - 5.0.0 bounce messages 
### AWS
Thanks to a AWS re:Post, I was able to resolve an issue that was preventing me from sending email using the AWS SES (Simple Email Service).

> Sending Email failed. Could not send email.
> Status: 5.0.0

A quick update to the SES Authorization policy to update the Principal to the Workmail service...
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "stmt1641172570046",
            "Effect": "Allow",
            "Principal": {
                "Service": "workmail.eu-west-1.amazonaws.com"
            },
            "Action": [
                "ses:*",
                "ses:SendBounce",
                "ses:SendRawEmail"
            ],
            "Resource": "arn:aws:ses:eu-west-1:XXXXXXXXXXXX:identity/x--v--x.com",
            "Condition": {}
        }
    ]
}
```
...and Voila! 

Working email outbound from SES!

Here's the [article](https://repost.aws/questions/QUXMqm3LNrS-StjWHt1zUcCg/aws-work-mail-cant-send-emails)

## 18th October 2022 - Passed my AWS Solutions Architect - Professional Exam 
### AWS
Passed my AWS Solutions Architect - Professional Exam !!!!
<div data-iframe-width="150" data-iframe-height="270" data-share-badge-id="3002aa4a-52f6-4ac7-926e-3e1714ea2f3f" data-share-badge-host="https://www.credly.com"></div><script type="text/javascript" async src="//cdn.credly.com/assets/utilities/embed.js"></script>

## 17th October 2022 - Took my AWS Solutions Architect - Professional Exam 
### AWS
Took my AWS Solutions Architect - Professional Exam 

## 23rd November 2021 - Shorter road to SA - Pro
### AWS
Completed my first course on AWS Skills Builder, which looks like a great platform for learning materials   
Amazon Transcribe   
 - Allows live realtime transcription of audio   
 - Custom vocabulary file supports    
 - Vocabulary filters can be removed from the transcription   
 - Ability to batch process   
 - Also adding a process flow to inculde kinesis data streams, lambda and    
 - Allows translation using AWS Translate   
 Signed up for AWS Partner Webinars on:   
 - Machine Learning on AWS   
 - Advanced Migrating to AWS   
 - Containers on AWS   
 
## 12th November 2021 - Shorter road to SA - Pro
### AWS
Watched the ["Disaster Recovery of Workloads on AWS | AWS Events"](https://youtu.be/cJZw5mrxryA)   
Mostly covers the information in the AWS Disaster Recovery whitepaper but with better visualisation   
- Multi-Site Active/Active   
- Warm Standby  
- Pilot Light   
- Backup / Restore   
AWS Customer Council   
I signed up to be part of the AWS Customer Council providing feedback on AWS services and releases.   
### Community
Experimenting with Obsidian which is a multi-platform note-taking application that supports better integration of notes using frameworks such as Zettelkasten.
Ideally I could tie this to an MKdocs instance and establish a publishing process to GitHub.   
GitHub Blog Input:
- Update Blog: GitHub
- Application: Obsidian
- Format: Markdown
- Text: Touchtyped

## 4th November 2021 - Shorter road to SA - Pro
### HomeLab
Began setting up the TuringPi and installed Hypriot on all 7 modules.   
Before installing ECS Anywhere and eventually EKS Anywhere (Once released for baremetal installations), I've decided to use the Jeff Geerling guide to install services using ansible playbooks.   


## 3rd November 2021 - Shorter road to SA - Pro
### Work 
Worked through some issues with a new CloudFront distribution:   
- The load balancer is required to be public facing for Cloudfront.  
- 403 errors can be the result of alternate names not being set in the distribution   
- If CloudFront is rewiriting the http request header, a policy is required to passthrough the http header   
There's more detail provided in [this StackOverflow post](https://stackoverflow.com/questions/69399672/how-to-have-an-aws-elb-forward-the-actual-host-name-to-the-target-group-instead):


>In CloudFront, you need to create a new origin request policy, not a cache policy:
>
>   * Open up CloudFront   
>   * Go to Policies (left nav)   
>   * Click the "Origin Request" tab   
>   * Click the "create origin request policy" button   
>   * Name the policy whatever you want, i.e., "my origin request policy"   
>   * Under "Origin request settings" > Headers: select "Include the following headers"   
>   * Under "Add header": check the "Host" option   
>   * Click the "Create" button   
>
>The policy will look like this:

![CFOriginRequestPolicy](/images/CFOriginRequestPolicy.png "CloudFrontOriginRequestPolicy")

>Once the new origin request policy has been created:
>
>   * Head back to the CloudFront distributions   
>   * Click your distribution's Id so you can edit it   
>   * Click the "Behaviors" tab   
>   * Select your behavior and edit   
>   * Scroll down to "Cache key and origin requests"   
>   * Make sure the "Cache policy and origin request policy (recommended)" is selected   
>   * Under the "Origin request policy - optional", select your new policy, i.e., "my origin request policy"   
>   * Save changes   
>
>The behavior will look like this (I'm using no caching for now to verify the ec2 instance is getting all the requests): 

![CFCacheKeyOriginRequests](/images/CFCacheKeyOriginRequests.png "CloudFrontCFCacheKeyOriginRequests")

>That's it.   
>The host header is now correctly passed through to the ELB and ec2 instance.   
>Nothing else needs to be done with the ELB.   
 
## 2nd November 2021 - Shorter road to SA - Pro
### Udemy
Completed the remaining review of the SA Practice exam. Worked through my answers and paraphrased the correct reasoning for questions I'd answered incorrectly   

## 1st November 2021 - Shorter road to SA - Pro
### Reading
Read "AWS for Solutions Architects" -  Chapter 4 covering IaaS, PaaS & SaaS and making informed decisions about which is best   
The later part of the chapter covered EC2 and S3 features, all things I was already aware of so more of a refresher    

## 31st October 2021 - Shorter road to SA - Pro
### Udemy
Completed first Jon Bonso "Solutions Architect Professional Practice Exam":   
- Overall the experience went well   
- Adjusting to the shorter timeframe per question was tricky   
- The longer questions and answers take more time to read   

## 27th October 2021 - Shorter road to SA - Pro
### AWS
Completed the fourth and final "Solution Architect Professional Journey" questions
- Again positive results    
- I left feedback that I would prefer more questions to be covered in each session   

## 20th October 2021 - Shorter road to SA - Pro
### Reading
Read for "AWS for Solutions Architects" -  Chapter 3 covering Storage in AWS   
### Udemy
Completed Section 6: Storage of the Stephane Maarek SA Pro Course   
### AWS
Completed the third "Solution Architect Professional Journey" questions    
- Much more positive results this time so hopefully a good sign   
### Youtube 
Watched the "Instagram system design" video and CAP theorum lecture on data consistency in data distributed systems
Interesting concepts considered, i need to understand more about Partition Tolerance as this wasn't covered in detail    
## 19th October 2021 - Shorter road to SA - Pro
### Udemy
Completed Section 5: Compute & Load Balancing of the Stephane Maarek SA Pro Course  
This covered the API Gateway and Route 53 mostly  
The "Comparisons of Solutions Architecture" will be worth a re-watch as there were some good points on system design  
### Youtube
I found a great youtube channel called "Gaurav Sen" on System Design  
An excellent overview of the architecture behind WhatsApp was covered  
It really made some of the puzzle pieces come together in my head RE:Large distributed systems   
### Community
GitHub Blog Input:
- Update Blog: GitHub
- Application: VI
- Format: Markdown
- Text: Touchtyped


## 18th October 2021 - Shorter road to SA - Pro
### Udemy
Went through the re-cap on ELBs from Section 5 of the Stephane Maarek SA Pro Udemy Course
### Community
GitHub Blog Input:  
- Update Blog: GitHub
- Application: VI 
- Format: Markdown
- Text: Touchtyped

## 16th October 2021 - Shorter road to SA - Pro
### HomeLab
- Installed Docker on a Debian LXC container and configured it to run Plex, Radarr and Sonarr   
- Built a VM running Home Assistant and began integrating devices  

## 15th October 2021 - Shorter road to SA - Pro
### Work
Discussed a new [feature](https://aws.amazon.com/blogs/networking-and-content-delivery/application-load-balancer-type-target-group-for-network-load-balancer/) of the AWS Network Load balancer released last month:
- The new setting allows a NLB to use an ALB as a target type
- I can already think of a possible integration for this with our corporate logging service  
### Community
GitHub Blog Phase One-point-Two:  
- Update Blog: GitHub
- Application: Web-based VSCode Editor
- Format: Markdown
- Text: Touchtyped

## 14th October 2021 - Shorter road to SA - Pro
### Work
Discussed out best practices for VPC networking and IPv4 address allocation 
### Udemy
Completed 2 hours of the Stephane Maarek SA Pro course on Udemy covering ECS and Lambda
### Reading
Read the second chapter of 'AWS for Solutions Architects' by Alberto Artosanchez
- It seemed to cover in detail various approaches to cloud migration 
- Which seems helpful in adopting the correct strategy to approach the project
- It reminded me of the AWS 7Rs
![AWS7Rs](/images/AWS7Rs.png "AWS 7R's")   
### Community
GitHub Blog Phase One-point-Two:  
- Update Blog: GitHub
- Application: Web-based VSCode Editor
- Format: Markdown
- Text: Touchtyped

## 13th October 2021 - Shorter road to SA - Pro
### AWS
Attended the second session of 4 in the  'AWS PartnerCast - AWS Solution Architect Professional Certification Journey' series
- Practice questions went better than last week
- Clearly there's a significant leap between SAA and SAP certifications to be bridged    
### Work
Discussed out best practices for VPC networking and IPv4 address allocation 
### Udemy
Completed 2 hours of the Stephane Maarek SA Pro course on Udemy
### Reading
Read the first chapter of 'AWS for Solutions Architects' by Alberto Artosanchez
### Community
GitHub Blog Phase One-point-Two:  
- Update Blog: GitHub
- Application: Web-based VSCode Editor
- Format: Markdown
- Text: Touchtyped

## 12th October 2021 - Shorter road to SA - Pro
### AWS
AWS Power Hour on Architecting will run  for 6 sessions starting Monday October 18th 2021
### Work
Discussions around Infrastructure services AWS account  
### Udemy
Completed Section 4 of 'Ultimate AWS Certified Solutions Architect Professional 2021' by Stephane Maarek
### Community
GitHub Blog Phase One-point-Two:  
- Update Blog: GitHub
- Application: Web-based VSCode Editor
- Format: Markdown
- Text: Touchtyped

## 6th October 2021 - Shorter road to SA - Pro
Switched focus after some downtime with a vacation, I'm gearing back up to continue my studies.  
### AWS
Attended the first session of 4 in the  'AWS PartnerCast - AWS Solution Architect Professional Certification Journey' series
- A few poor decisions on the quiz questions but optimistic my skills will improve with practice

## 1st October 2021 - Shorter road to SA - Pro
Switched focus after some downtime with a vacation, I'm gearing back up to continue my studies.  
Given AWS are offering a four week "AWS Solution Architect Professional Certification Journey",  
I've decided to focus on the Solutions Architect Professional qualification and put the DevOps 
Pro study on hold for now.  

## 12th July 2021 - Adv. Architecting On AWS
### AWS
Day 3 - Place holder for Notes / Observations

## 9th July 2021 - Adv. Architecting On AWS
### AWS
Day 2 - Place holder for Notes / Observations

## 8th Oct 2021 - Adv. Architecting On AWS
### AWS
Day 1 - Place holder for Notes / Observations

## 6th May 2021
### RedHat
Completed the "RH024 - Red Hat Enterprise Linux Technical Overview" and would like to practice by using vimtutor in future.
### AWS
Watched the "Amazon Linux 2 Deep Dive" on Youtube to better understand the OS AWS recommend for Linux on AWS Cloud. 

## 5th May 2021 - Long road to DevOps
### Udemy
Read a blog post on "Implementing GitFlow using AWS CodePipeline, AWS CodeCommit, AWS Code Build and AWS CodeDeploy" by Ashish Gore.  
I followed in up with some videos on best practices for using GitFlow.  
### Work
Worked through some Systems manager configuration and proposed using session manager to relieve SSH management burden and provide  
a managed authentication platform using an existing identity provider. Removed a CloudFormation template and updated an Iam role.  

## 4th May 2021 - Long road to DevOps
### Udemy
I completed more of the DevOps course covering the CodePipeline in detail.
### Work
Began work on a CloudFormation template to deploy a Tableau Server.
### RedHat
Watched a video on Jenkins pipelines. Related to Kubernetes cluster deployments.
### Community
GitHub Blog Phase One-point-One:  
- Update Blog: Terminal \ Git
- Application: VI
- Format: Markdown
- Text: Touchtyped
Fixed some errors with multiple SSH keys with config file permissions 
### Instruqt
Discovered Instruqt and completed a short Ansible Tower course

## 29th April 2021 - Long road to DevOps
### Udemy
I completed more or of the DevOps course covering the CodeDeploy material.
### Work
Managed to get an early start on the day by working on Codebuild. A few more steps configured including a webhook to launch the   
build when code is pushed to the repo.  
Followed the SoftwareDev demo of Terraform / Codebuild pipeline and hoping to get a chance to discuss it in more detail  
### AWS
1pm course on managing Microsoft platforms on AWS - AWS Migration Hub and Server Migration Service
Community
Need to start pushing blog to GitHub Page

## 28th April 2021 - Next challenge
DevOps Pro or SA Pro
Began the process of figuring out which cert to try for next 
### Udemy
Watched the first part of the DevOps Pro course by Stephane Maarek. Covered CodeCommit and CodeBuild.
### AWS 
Started doing the sample questions for SA Pro and in some ways it wasn’t as tricky as I was expecting.
### Work
Started building a ci pipeline with codebuild using github as a source.

## 27th April 2021 - Decompress
### LinkedIn Learning
Completed the AWS SA course by Tom Carpenter
### Work
Looked into blue/green deployment on elastic beanstalk. Started the trusted advisor audit across the accounts.   
Reviewed current AWS config settings in the corp account.   
### AWS
Got my score! That means for all three associate certs I've scored over 900.  
I've requested be put forward for the 'Advanced Architecting On AWS' QA course for training.  

## 26th April 2021 - SysOps Certified
### Youtube
Completed the last to CQ episodes 
### Brainscape
On the way to the exam went through the flashcards
### AWS
The exam went okay, it was nice to have a scratch sheet to write things and the climate controlled office was preferable to my previous online experience.
Thankfully, I had plenty of time and was able to finish early.  
Although I'd flagged or made notes on a few questions, I had ample time to revisit and submit revised answers.  
### LinkedIn Learning
Completed the Shyam Raj Course on 'AWS: Monitoring and Reporting'
- Great for AWS Config settings 
- RDS Event triggers
Started Enterprise security by Sharif Nijim 
- Ideas around separation of duties:
    Engineering has Root passwords
    Security holds the MFA Hardware tokens

## 25th April 2021 - Road to SysOps
Study Materials:
- AWS Practice Exam - 30 Mins
- Jon Bonso Exam #6
- Monitoring section
- Stephane Maarek course - 'Exam prep & Monitoring'
- Read FAQs
- Read Study notes  
### Udemy
Completed  ‘AWS Certified SysOps Administrator Associate Practice Exam 5’ by Jon Bonso.
Worryingly I didn’t do too well. 
Completed other sections of the Stephane Maarek course
Re-sat the Stephane Maarek practice exam, that I'd initially failed at the start of my study
### Youtube
Completed several CQ episodes on youtube
### AWS 
Completed the Sample Questions
Sat the AWS Practice exam and scored 80%
### Quizlet / Brainscape
Created a set of flashcards based on the Sysops Cheatsheet by Jon Bonso

## 24th April 2021 - Road to SysOps
### Udemy
Completed  ‘AWS Certified SysOps Administrator Associate Practice Exam 4’ by Jon Bonso.  
I passed but felt I fell foul to some wording that seemed ambiguous.  
Followed it up by typing up my incorrect answers into a Google Doc to supplement my learning material.  
### LinkedIn Learning
Completed the ‘Exam Tips: AWS Certified SysOps Administrator’ lecture by Sharif Nijim.  
- I'd mostly covered this material previously but good as a refesher  
- The CloudWatch visual representation was a great touch  
Started the first section of 'AWS Monitoring and Reporting' by Shyam Raj  
- This goes into detail on a considerable part of the exam - 22%  
- Completed the section on CloudWatch and the end of section quiz   
### AWS Study Materials
Completed course ‘AWS Exam readiness'  
WS Sample Exam Questions and did fine   
### Quizlet
32 flashcards of the 177 by beezy_bob 

## 23rd April 2021 - Road to SysOps
### LinkedIn Learning
Watched the start of Tom Carpenter's Solutions Architect 7 application deployment course.  
It's an enjoyable format watching Tom clearly explain the content.  
Much more engaging than some of the PowerPoint online content  
 - I Liked the breakdown of cloudfront uses  
 - Covered Swf in context  
 - Nice step function example  
 - Content type  
 - Rekognition  
 - Thumbnail generation  
 - Sqs and sns  
 - Kinesis types  

Completed "AWS Administration: Tips and Tricks" it was basic content but practical in it's broad real life use cases. 
 - Various instructors  
 - Short lectures  
 - Easily digestible  
 - Added cloud applications to my profile  

Finished the 'AWS: Deploying and Provisioning' by Brandon Rich  
It's well explained with some great examples that are less common than some other lectures  
Leans more heavily on Ruby but very good to see more detailed examples  
Using lambda for custom resources in Cloudformation  
Ruby application deployed with Elastic Beanstalk  
Some more focus on using the AWS cli for Elastic Beanstalk  
The opsworks demo provided good insights into the platforms strengths  
Code deploy is another lesser demoed technology  
Cloud9 looks like a easy way to standardise the ide platform to provide a unified experience to developers  
Codestar is a great tool but in some ways it seems too easy to deploy a ci/cd pipeline  

### QwikLabs
Introduction to Amazon CloudFront  
- Created a new Amazon CloudFront distribution  
- Used your Amazon CloudFront distribution to serve an image file  
- Deleted your Amazon CloudFront distribution when it is no longer required  
Introduction to AWS Lambda  
- Created an AWS Lambda function  
- Configured an Amazon S3 bucket as a Lambda Event Source  
- Triggered a Lambda function by uploading an object to Amazon S3  
- Monitored AWS Lambda S3 functions through Amazon CloudWatch Log  
Introduction to AWS Key Management Service  
- Created an Encryption Key  
- Created an S3 bucket with CloudTrail logging functions  
- Encrypted and image and stored it in your S3 bucket  
- Viewed the encrypted image using the AWS Management Console  
- Monitored encryption key usage using CloudTrail  
- Managed encryption keys for users and roles   
### Community
Setup a github page and started blogging.  
GitHub Blog Phase One:  
- Update Blog: Terminal \ Git  
- Application: VI  
- Format: HTML  
- Text: Touchtyped   
Blog updates: End each post with timestamp / OS / Text editor / Location (City) /  WPM  

## 22nd April 2021 - Road to SysOps
### LinkedIn Learning
Completed the 4 hr 'High Availability' lecture by Sharif Nijim - Very good overall  
Versioning is required on both buckets for Cross region replication  
EBS volumes can now be attached to multiple instances  
Elasticache versions are slightly behind on AWS  
Amazon Keyspaces is the AWS implementation of Apache Cassandra  
- Keyspaces is not yet multi-region  
Added High Availability to my profile  
Started AWS: Deployment and Provisioning by Brandon Rich   
### QwikLabs
Used Qwiklabs for the first time today, it's very good  
Some of the labs seemed dated but the experience of setting things in the AWS console was good  
Tempted by the Advantage subscription for at least a month  
Introduction to AWS Identity and Access Management (IAM)  
- Explored pre-created IAM users and groups  
- Inspected IAM policies as applied to the pre-created groups  
- Followed a real-world scenario, adding users to groups with specific capabilities enabled  
- Located and used the IAM sign-in URL  
- Experimented with the effects of policies on service access  
Introduction to Amazon DynamoDB  
- Create an Amazon DynamoDB table  
- Enter data into an Amazon DynamoDB table  
- Query an Amazon DynamoDB table  
- Delete an Amazon DynamoDB table  
Introduction to Amazon Simple Storage Service (S3)  
- Create a bucket in Amazon S3  
- Add an object to your bucket  
- Manage access permissions on an object  
- Create a bucket policy  
- Use bucket versioning  
Introduction to Amazon API Gateway  
- Create an AWS Lambda function  
- Create an Amazon API Gateway endpoints  
- Debug API Gateway and Lambda with Amazon CloudWatch    
### Work
Suggested the use of two Amazon snowball devices for moving 100TB of data to S3  
Also, noted that AWS data pipeline could be helpful  
Worked on a proof of concept for PreSigned Urls using the Python handler in AWS lambda   
### Community
Updated my Meetup profile for AWS focus and setup notifications to my primary email address 

 
[![AdamP's GitHub stats](https://github-readme-stats.vercel.app/api?username=adamp-github)](https://github.com/adamp-github)
