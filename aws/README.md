# AWS CLI

[Get IP address of instance](#get-ip-address-of-instance)  
[List all running ec2s](List-all-running-ec2s)  


#### Get IP address of instance  
```aws ec2 describe-instances --filters "Name=instance-state-name,Values=running" "Name=tag:Name,Values=<INSTANCE_NAME>" --query 'Reservations[*].Instances[*].[PrivateIpAddress, PublicIpAddress]'```

#### List all running ec2s
```aws --output text ec2 describe-instances --filters "Name=instance-state-name,Values=running" --query 'Reservations[].Instances[].[Tags[?Key==`Name`].Value[]]'```
