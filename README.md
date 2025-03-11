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
CFT will allow you to write your infrastructure as Code. We will just write i need VPC, S3 and other config which required in terms of templating language i.e Json or YAML.
## Infrastructure as Code (IaC)
CFT has a very good documentation, we can go to CFT doc and see how to write Json\YAML format this way we can write our Infra as Code. This code can be shall or python or any of the Json]YAML templet as we are not doing manually through the UI  where we have automated it can be simple template (Json\YAML) or it can be any scripting mechanism which is called Infrastructure as Code.
There are so many IaC tools available in Market.
For AWS ---> Cloud Formation Template
For Azure ----> Azure Resource Manager -- If you go to ARM Template we can see how to provide Json syntax and YAML syntax. If we want to Azure VM, AKS Cluster or Blob storge we can put in the format in ARM Template then it will make a request to Azure ant it will create out infra. 
If we are working on open stack they have Heat template.
There are multiple tools in the market, for each provider the developer of the provider has provided the template.
AWS -- Cloud Formation Template
Azure -- Azure Resource Manager
Open Stack -- Heat Template
## Why Terraform:
Organization will use AWS, Azure, GCP, Open stack we need to learn many tools to automate the things but Terraform will solve the problems without learning multiple tools.
Terraform will come up with universal approach that means we dont need to learn multiple tools just learn T\F. 
Just tell to Terraform i.e create resource in Azure or AWS or GCP then it will create.Terraform is very important because irrespective of provider which we can use
How to learn Terraform templating language Harshicorp language Template.
Competitors to Terraform --Cross Plane and so many tools but Terraform started the universal approach where one Terraform using the concept of API as code internally 
Irresptive of providers API as code will directly talk to provider, HCL will convert the code to required API like Azure API or AWS API and apply this to create infra. Terraform has very good community. Terraform has easier code 
## How to Install Terraform.
We can directly intall it from browser for windows\Linux\Unix\Mac https://releases.hashicorp.com/terraform/1.11.1/terraform_1.11.1_windows_386.zip.
or If we dont have any laptop or resource to install
Login to your GitHub account
Click on the Profile Icon to the top right
Click on "your codespaces" and it will provide 60 hours (2CPU 4GB RAM)free time for a Month
Codespaces will provide you a virtual machine with Ubuntu and VS Code by default.
Follow the steps provided in Download to install Terraform.
## Code Space Configuration
When we click on Code space it will take time for configuration for first time to create code space, its like a single virtual machine it is actually a continer.
to check Terraform Version use the command --> Terraform --Version, by default Terraform will not install
to check AWS Version use the command --> aws --Version, by default aws will not be iinstalled
## Github code space
Github code space is a sand box environment or we can consider as a container environment
## Terraform installation in Code Space.
Go to Search bar type  >dev then we can able to see Code Spaces :Add Dev Container Configuration File it will install AWS and Terraform in our github code space environment
Click on Modify your active configuration and search for Terraform then you will find verfied mark in Terraform,tflint,TFGrunt devcontainers then select and click OK then select keep defaults.
Then will get new file been added like devcontainer.json where will see terraform configuration.
before installing terraform we need to install aws, again go to search type >dev then add dev container configuration file --> click on Modify your active configuration --> search for aws --> First one select AWS CLI devcontainers which we ca see as verified symbol click OK --> keep default
Final step search >rebuild and click on Rebuild container --> we will get rebuild popup then we need to click on it--> it is trying to rebuild the devcontainer then we will get new container, it will install terraform AWS CLI
Note: When we practice terraform we also need to install Visual Studio
Now we can see Terraform and AWS installed in our devcontainer
## Configure Terraform for AWS (In Org we can use IAM user)
Login to AWS console go to root user --> security Credentials --> fetrch the information of aws access keys, if we have old keys delete and create new key then it will create secrete access key along with access key.
## Step 1
Go to VS code or Terminal in code space run the command ---> aws configure
It will ask AWS access Key ID --> enter new access key
then it will ask AWS secrete access key ID --> enter new secrete access key id 
it will ask Default region name --> enter the region which we want to create resource for ex us-east-1
it will ask default output format --> enter json
Now aws is configured for verification run the command ---> aws S3 ls then we will see all S3 bucket details 
## Step 2
We will write a Terraform Provider.tf file or Terraform file
Go to Github reposiroty Every project we need to upload file,we are authenticate to aws and create ec2 instance.
we can create file called main.tf in that what we need to do is firsly we explain Terraform when ever we arite a code in T\F it does not understand are we writing a script for automating AWS, Azure or GCP
We need to create a file in our VS environment or in Terminal like main.tf file because it is main configuration file. 
Inside main.tf first thing we need to write is what is our provider configuration
ex: Provider "aws" {
Region = "us-east-1"
}
the above step verify the Terraform does have the access to aws to run a particular command
After that we want to provide resource which want to create
ex: Resource "aws_instance" {
ami = "appropriate ami id"
Instane_type = "t2.micro"
subnet_id = "Subnet-XXXX"
key_name = "aws_login"
}
We can copy it from terraform documentation (search in google terrform aws then go to AWS provider Hashicorp )
In Hashicorp documentation search for syntax, in the filter search for ec2 under ec2 we want to create ec2 instance --> awsinstance
Note : in Harshicorp Doc we can find example syntax for all resource creation
We have provided aws security details using --> aws configure command
after this we need to run bunch of Terraform commands it will help you to configure infra
## Terraform Commands
1. Terraform init --- it will initialize the configurtion (We need to provide right path)
2. ls --> it will display all the directories
3. Terraform Plan -- it will shown us the configurtion\code which we are going to apply
4. Terraform apply -- to execute the commands
5. Terraform destroy -- remove or delete the created configuration
6. terraform.tfstate -- to record what ever is going to create
for ami id -- Go to aws console and click on launch instance then select OS flavour then will get the ami id
we can install Hashicorp Terraform plugin and Hashicorp HCL extension

## Terraform Life cycle
1. Terraform init
2. Terraform Plan
3. Terraform state
4. Terraform destroy

















Q-1 How AWS\GCP\Azure is linked to Terraform --->Terraform integrates with AWS, GCP, and Azure through provider plugins, allowing you to manage infrastructure in these cloud environments. You write configuration files, define the desired state of resources, and then use Terraform commands to create, update, and manage those resources across various cloud platforms. The flexibility of Terraform in supporting multiple providers enables seamless multi-cloud and hybrid cloud management.
Q-2 What are the different providers TF support ---> Categorized to Official (aws,azure,gcp,kubernities), partner  , community
Q-3 How many Providers can be deployed in single code ---> There is no fixed limit to the number of providers you can use in a single Terraform configuration. You can deploy resources across different cloud providers like AWS, Azure, GCP, and others, using multiple provider blocks, optionally with aliases to manage different accounts, regions, or subscriptions. However, when working with multiple providers, always ensure that the configuration and state management are handled appropriately for the complexity of your infrastructure.
Q-4 Can we deploy 2 VM's in 2 diffetrent regions at a time in a single code
Q-5 How to destroy a single instance 
Q-6 What is the difference b\w input and output variable
Q-7 How many keys we can generate a day
Q-8 Explain complete life cycle of Terraform
