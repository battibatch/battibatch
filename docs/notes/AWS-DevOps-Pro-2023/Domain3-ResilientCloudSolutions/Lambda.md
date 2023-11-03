# Lambda

## Versions and Aliases
usually start w/$LATEST

publish immutable versions of lambda functions
Each version is independent, own ARN
Each version can be accessed

Alias give users stable endpoint and point to different versions
i.e. dev, test, prod alias
Alias is mutable as it changes versions

Aliases enable Canary deployments by assigning weights

Enable stable configs of trigger and destination

Alias cannot reference another alias

## Environment Vars
key value pairs
adjust function w/o updatei
