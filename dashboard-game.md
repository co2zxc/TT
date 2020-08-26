# Dashboard Usage Guide

This guide will explain how to use this dashboard and how to interact with your AWS Account.


## Sections
The dashboard is broken into various sections which you will utilize throughout the game.  
![alt text](https://s3.amazonaws.com/ee-assets-prod-us-east-1/engine/dashboard.png)

1. **Team Stats**
	1. **Score** Your cumulative score throughout the day
	2. **Rank** Your overall rank amongst all teams
	3. **Trend** This is a sumation of all the point actions against your team for the last minute.  You want this number to be positive.  If this number is negative or is starting to drop, you might want to investigate to see if you're losing points!

2. **Game Information**
	1. **Set Team Name** This button will allow you to specify your team name.  Keep in mind you only get to do this once, so choose wisely!
	2. **Score Events** This will allow you to see all the score events for your team.  See the [Score Events](#score-events) section below which will provide more details.
	3. **Scoreboard** This will allow you to see the scores for all teams in the events.
	4. **AWS Console** This will give you access to your AWS Account.  See the [AWS Account](#the-aws-account) section below which will give you more information on restrictions within the account, credentials, etc.
	5. **SSH Key** This will allow you to view and download the SSH Keypair PEM file to SSH into EC2 instances as required.


## Score Events
![alt text](https://s3.amazonaws.com/ee-assets-prod-us-east-1/engine/score_events.png)

This page will show all the recent score events for your team.  We encourage you to look at this frequently to understand what's happening within the game.  You can see modules where you're accruing points, and places where you're losing points.  For the items that are deducting points, take a look at the reasons which can help explain what you are doing incorrectly and a hint at how to resolve this.


## The AWS Account
For this session, we are providing you access to an AWS Account.  The role that we have provided your team has limited permissions which will restrict you to the services and API calls that you need.  These accounts are temporary and access will be revoked after the session, at which time all resources will be deleted.

By clicking the "AWS Console" button above in the Game Inforamtion section, you will receive STS credentials for programmatic access to your AWS Account and a federated link to get into the AWS Console.

* **Environment Variables** For programmatic access to your AWS Account we've provided you with STS credentials you can use to access your account.  In order to use these, paste all four items into your terminal window.  If you choose to create an AWS profile, make sure you use all three components (access key, secret key, **and** the session token).
* **Federated Link** Click the **Open Link** or **Copy Link** buttons to get acess to the AWS Console

**IAM Service Roles**  Some AWS resources, like AWS Lambda functions, Amazon ECS Clusters, etc. all require an IAM role to function.  The role that you are provided access to has all the permissions that you will require throughout the day.  It also has an assume role policy that allows all the AWS Services you'll use throughout the day to assume this role.  When you create things like Lambda functions, ECS Clusters, Code Pipelines, etc. **do not** try and create a new role as this will fail.  Choose the option to **select an existing role** and choose the **player_role**.

## Modules
Modules are what you will spend most of your time on throughout the day.  Modules focus on a specific task and require you to solve various challenges to earn points.  Within modules, there are checkpoints which will help you track your progress against these milestones throughout the day.  By achieving checkpoints, you will earn chunks of points.  

In addition to checkpoints, modules also will allow you to accrue points over time by maintaining infrastructure or continuing to process items.  These items give you smaller amounts of points as compared to checkpoints, but due to their frequency and continued nature can help you amass large amounts of points.  Conversely if you have something misconfigured or aren't continuing to process items you can lose large amounts of points over time.

![alt text](https://s3.amazonaws.com/ee-assets-prod-us-east-1/engine/modules.png)

Each module will have it's own card on the dashboard, that will provide you with information on how to interact with it and earn points.

1. **Score** At the top of the dashboard, we provide you with your overall score, but this provides you with the score for this particular module.
2. **Trend**  Like the Score above, this shows you your score trend for ths individual module.  Take a look at all the score trends for each module, as this can tell you the modules you might be losing points on.
3. **Readme**  In order to understand what you're supposed to be doing and what the various challenges are, view the Readme.  This will provide the background into what you'll be working on, links to various resources and documentation, hints, etc.
3. **Outputs** Modules will need to give you information as they progress.  These can be things like AWS Account IDs to trust, SNS Topic Arns to publish to, various endpoints you'll need to hit, etc.  Use this section to obtain this information and copy these values.
4. **Inputs** Throughout the day you will interact with modules.  They might provide you with an answer to a question, or a code for completing a challenge, or to indicate you're ready to move onto the next stage.  Inputs provide you with a way to send this information back to a module.
