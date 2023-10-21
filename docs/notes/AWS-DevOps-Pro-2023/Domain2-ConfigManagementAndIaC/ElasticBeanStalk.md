# Elastic Beanstalk

## Overview
3 tier web app
LB -> ASG -> RDS/Cache

As a developer is complex to:
* manage infra
* deploy code
* configure LB, DB, etc.
* Scale

Most apps have same architecture

Beanstalk give a dev centric view to deploy and app
managed service
automatically handles the capacity, LB, scaling, monitoring, instance config, etc. 

dev only to manage the app code

Still have control over the config
Beanstalk is free, but pay for components

## Components

Application - collection of components (envs, version, config, etc.) 
App version - iteration of app code 
Environment - 
* collection of AWS resources running app verion (1 version at a time)
* Tiers - web server env tiers, worker env tier, etc.
* can have multiple envs (dev, test, prod)

Create app > Upload version > launch env > manage env 
update version > deploy new version

web server vs worker
* no users access to worker
SQS to manage work
web manage work sent to worker

## Deployment modes
* single instance - 1 ec2
* HA w/ LB - ASGs and RDS hot/standby instances.



