# DynamoDB

## Overview
Full managed 
HA
Replication across Multiple AZ
NoSQL DB - not relational w/ transation support
scales to massive workloads, distributed DB
millions of requests per second, trillions or rows, 100s of TBs
fast and consistent
* Single digit millisecond performance
Integrated with IAM for security, authz and admin 
low cost and ags
no maintenance

Standard table class

## Basics
DDB is made of tables
Each table has a primary Key
Each table can have infinite number of items (rows) 
each item has attributes (Can be added over time, can be null) 
Max item size is 400KB
Data types supported: 
* Scaler types - string, number, binary, boolean, null 
* Doc type - List, maps
* Set types - string set, number set, binary set

DDB you can rapidly evolve schemas

Partition Key, sort key

### Capacity Modes
Controller how you manage tables capacity
Provisioned Mode (default) 
* specify the number of read/writes/s
* plan capacity in advance
* pay for provisioned Read Capacity Unites (RCU) and Write capacity Units (WCU)
* Possible to asg mode for RCU and WCU
* Works great for smooth loads that are predictable or save money

On-demand mode
* read/writes scale automativcally
* no RCU or WCU, so no planning needed
* Pay for what you used, more expensive
* great for unpredictable or steep sudden spikes
    * 1000s to 1millions requests in a minute


