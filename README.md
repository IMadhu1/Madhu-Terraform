# Madhu-Terraform
## Day-1 
Terraform advantages
We can automate the resource deployment in any cloud providers (AWS, Azure, GCP)
Lets say you are a Devops Eng and given a task to create S3 bucket for AWS. Go to AWS console then provide  your cred (username and password) to authenticate AWS and search for S3 service and go there and provide all the required details (name, location and etc)and create it for this hardly it will take 5 mins.
If you get similar kind of requests from multiple teams it will take time using UI with manual efforts. To avoid this we can use programmatic approach through AWS CLI, AWS API.
For every resource in aws like S3 bucket or instance it will develop API, using any programming language we can talk to aws services programmatic language trough the API
 which means you can call to aws instead of login to aws for particular progam.
 You can use either CLI or API write code in single line (python)to create S3 bucket using this we can create multiple resource with in fraction of seconds. It can reduce the manual efforts. For that we need programming language.
If we ant to create VPC, VPC Config, EC2 instance which is highly available and S3 bucket end point of VPC config, if we want to do all of these things we need to have a good programming language.
The cloud providers like aws says to Devops eng that some of you dont have good programming language then what we can do is we will do heavy lifting and will introduce Cloud Formation Template (CFT). 
In CFT we can write a template either Json\YAML, most of the people in the industry they know Json\YAML as its standard template to share the output or to provide input to any tools.




Q-1 How AWS\GCP\Azure is linked to Terraform 
Q-2 What are the different providers TF support --Categorized to Official (aws,azure,gcp,kubernities), partner  , community
Q-3 How many Providers can be deployed in single code 
Q-4 Can we deploy 2 VM's in 2 diffetrent regions at a time in a single code
Q-5 How to destroy a single instance 
Q-6 What is the difference b\w input and output variable
Q-7 How many keys we can generate a day
Q-8 Explain complete life cycle of Terraform
