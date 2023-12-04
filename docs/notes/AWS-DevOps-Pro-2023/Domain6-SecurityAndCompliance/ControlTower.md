# AWS Control Tower
Easy way to set up and govern seure and compliant multi-account AWS Env based on best practices

Benefits: 
* Automate the set up of your environment in a few clicks
* Automate ongoing policy management using guardrails
* detect policy violations
* monitor compliance through an interactive dashboard

AWS Control Tower runs on top of AWS Orgs
* automatically sets up AWS Orgs ot organize accounts and implement SCPs

## Account Facotry
automates account provisioning
Enables you to create pre-approved baselines and config options for AWS accounts
uses AWS Service Catalog to provision new AWS Accounts

use case: create a new account that automatically is configured through On prem AD

## Guardrails
provides ongoing governance for Control Tower env (AWS Accounts) 
Preventative - using SCPs
Detective - using AWS COnfig

### Levels of Guardrails
Mandatory
* auto enabled and enforced by AWS COntrol Tower

Strongly recommended
* Based on AWS best practices

Elective
* Common used by enterprise