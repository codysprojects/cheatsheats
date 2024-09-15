# AWS CLI

[Get IP address of instance](#get-ip-address-of-instance)  
[List all running ec2s](#list-all-running-ec2s)  
[Get the latest Linux ami](#get-the-latest-linux-ami)


#### Get IP address of instance  
```aws ec2 describe-instances --filters "Name=instance-state-name,Values=running" "Name=tag:Name,Values=<INSTANCE_NAME>" --query 'Reservations[*].Instances[*].[PrivateIpAddress, PublicIpAddress]'```

#### List all running ec2s
```aws --output text ec2 describe-instances --filters "Name=instance-state-name,Values=running" --query 'Reservations[].Instances[].[Tags[?Key==`Name`].Value[]]'```

### Get the latest Linux ami
    aws ec2 describe-images --region "<REGION>" --owners amazon --filters 'Name=architecture,Values=x86_64' 'Name=name,Values=al2023-ami-2023*' --query 'sort_by(Images, &CreationDate)[-1].ImageId'
