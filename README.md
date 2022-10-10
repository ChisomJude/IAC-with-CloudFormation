# IAC-with-CloudFormation
## Project Title - Deploy a high-availability web app using CloudFormation

This project contains Cloud Formation Templates to deploy Cloud infrastructure to AWS
<img src="Architectural Diagram.png" width="800" height="400">

#### Resources Deployed
 - VPC 
 - Internet Gateway
 - Private and Public Subnets 
 - NAT Gateway
 - Routes
 - Application load balancer
 - Autoscaling group 
 - EC2
 - Launch Configuration
 - IAM Policy
 
> This deploy a website accessible via the Application loadbalancer url.<br>
>  <http://chiso-webap-14bujaxh7rwwt-995436831.us-east-1.elb.amazonaws.com/> <br>
> This aws resource will be delete soon 

#### How to deploy the 
First deploy the Network infrastructure using the create-stack command

```
    aws cloudformation create-stack \
    	--stack-name "stackName" \
    	--template-body file://network.yml \
    	--parameters file://network.json \
    	--region=us-east-1 \
    	--capabilities "CAPABILITY_IAM" "CAPABILITY_NAMED_IAM"
```

Once this is successfull, then you create another stack for the Servers using same command

```
    aws cloudformation create-stack \
    	--stack-name "stackName2" \
    	--template-body file://servers.yml \
    	--parameters file://servers.json \
    	--region=us-east-1 \
    	--capabilities "CAPABILITY_IAM" "CAPABILITY_NAMED_IAM"
```

Incase of any error or need to delete, you can run either run the update-stack cmdlet in update.sh or delete stack using the delete.sh cmdlet

To successfully run AWS cmdlet on our complete, ensure you have AWS CLi installed, confirm this using `AWS --version`. Also navigate to the AWS portal and create an IAM user with programmatic Access, copy out your secret and IAM user ID then run the command below and follow prompt to enter your AWS Access Secrets and User ID, default region and output templete. (The last two can be empty to retain default) 

`aws configure --profile default`

You can confirm by getting list of users - `aws iam list-users`








