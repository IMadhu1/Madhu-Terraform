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
Click on Modify your active configuration and search for Terraform then you will find verified mark in Terraform,tflint,TFGrunt devcontainers then select and click OK then select keep defaults.
Then will get new file been added like devcontainer.json where will see terraform configuration.
before installing terraform we need to install aws, again go to search type >dev then add dev container configuration file --> click on Modify your active configuration --> search for aws --> First one select AWS CLI devcontainers which we can see as verified symbol click OK --> keep default
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
2. Terraform plan
3. Terraform apply
4. Terraform destroy

## IMP TOPICS
Terraform installation
Terraform Version
Terraform structure
Provider "AWS\Azure\GCP"
Region "us-east-1\West Europe" 
Define Resource ""
Define Variable 
Define Output
main.tf
variable.tf
provider.tf
output.tf
Module

Module Terraform 
1 Linux, 1 Windows VM, 1 storage account, 1 key vault, 1 Sql
create 2 users one should have VM contributor vm, key vault and storage and 1 should have sql contributor
provider "aws"

## Day 2
Will learn what is provider in detail, different types of providers and configuration of Providers.
Providers for multiple regions and providers for multiple cloud i.e. hybrid cloud
How to write resource in Terraform and what exactly is resources
We can understand variable in tf and input\output variables tfvars 
Conditional expressions and functions
Finally debugging and formatting in tf

## Providers
When we created EC2 instance on the aws platform what we wrote first thing in main.tf file is the Provider bloc, inside proider in "aws" and configuration and other access keys inside brace etc
but if we dont mention these details in provider and proceeding with resource creation followed by the following code
Provider "aws" {
configuration of Provider like
region = "us-east-1"
acccess secrete key etc
}
resource "aws_instance" "Example"{
ami_id = "ami-id"
instance_type = "t2.micro"
}

If we run terraform init it will get succeeded, if we run terraform apply command how it will apply or understand where it has to create resource, how to athenticate to particular provider. All of these info will be available in Provider block.
Provider is nothing but its a plugin that helps terraform to understand that where it has to create the infrastructure. So it acts as a Medium for tf to understand where the resource or entire project has to be created. Without provider it is not possible.
What if we want to create infra on Azure\GCP\Alibaba Cloud instead of AWS. 
Where will understand how to configure these provider, just we can go to terraform providers page and there are hundreds of providers, tf provides so many providers categorized into 3 types.

Official Providers --> the one which Harshicorp actively maintains as Harshicorp is creator of tf they actively maintain the providers like AWS, Azure, GCP, Kubernets
Partner Providers --> Partner providers are these one where lets say Alibaba cloud harshicorp didnt create provider for them, what alibaba cloud said is okay we will write resources we will tell tf how to authenticate or how to create infra on us and we will actively maintain this particular provider. 
Community Providers --> Community providers are something where you and me can create the entire configuration and open source will maintin these providers, there is no official packing up by harshicorm or partner provider or any partners of harchicorp.
In our organization we tyring to automate things in different like apart from AWS, Azure, GCP. If we are using different cloud or creating infra somewhere else then we have to make sure atleast if it is community provider there are some active contribution that are made to it. If there are no active contribution made then it is not that much suggested to user tf provider apart from that if we can user Official and partner no problem at all.
Interview point of view.
1. Multiregion setup of tf 
2. Multiple cloud i.e. Hybrid cloud configuration of tf

## Multi Region
Lets say we are usin aws and we want to automate the infrastructure us-east-1 as well as us-west-2 then we will srite two provider bolck instead of one provider block.
In the First provider block we will say provider is aws and will use keyword as alias  and for us-west-2 again will write provider block and will create different alias, 
ex:Provider 1
Provider "aws" {
  alias = "us-east-1"
  region = "us-east-1"
  }
  Provider 2
 Provider "aws" {
  alias = "us-west-2"
  region = "us-west-2"
  }
when we try to create ec2 instance what we have to do is we have to writen is  resource ec2 instance example and we provided what is the ami and instance type, apart from that when you want to create resource in multiple regions you can create alias for your provider and within that particular resource block we can say provider = aws.the name of the alias. This is how we can setup tf for multiregion
ex: resource "aws_instance" "Example name" {
    ami = "ami id"
    instance_type = "t2.micro"
    Provider = "aws.us-east-1"
    }
resource "aws_instance" "Example name" {
    ami = "ami id"
    instance_type = "t2.micro"
    Provider = "aws.us-west-2"
    }

## MultiCloud or Hybrid cloud 
If organizations will use Hybrid cloud in such cases sa same the above we will configure providers with different names
AWS has the provider name as aws and Azure has the provider name as Azurerm, we can find the provider names in official document. Without go through the official document we cant know the provider names.
Provider "aws"{
Region = "us-east-1"
}
Provider "Azurerm" {
Subcription_id = "your Azure-subcription-id"
Tenant_id = "Azure-tenant-id"
Client_secrete = "Azure-secrete-id"
Client_id = "Azure-Client-id"
}
resource "aws-instance" "Example name" {
ami-id = "ami.id name"
instance_type = "t2.micro"
}
resource "Azurerm-virtual-machine" "example name" {
name = "example-vm"
location = "west europe"
size = "Standard_A1"
}

## Variables
Variables are very quite common, any programming language that we are trying to learn or any scripting we will use variables
Advantages of Variables: Variable is used to paramaterize, they can be used as Params to pass values to our project. 
Same in tf, lets say we write a standard tf project and this tf project is used by one particular team. Later other team comes up with the same request so if you are hard coding values in the tf, in main.tf we have hard coded the ami values and instance_type value. But this is not the good practice beacuse if some other team as a DevOps person we will support multiple teams.
If some other team comes and tells us they need tf coe to create EC2 instance, we have already one code then why we need to raise again and again, if we are hard coding the ami value and instance_type value that is what we will do, we will rewrite this entire project for another team so to solve this problem what will do instead of providing the ami value as string we can replace with variable and instead of writing instance value  we can replace with variable.
In TF there are 2 types of variables --> 1. Input Variable , 2. Output Variable
Input Variable : If we want to pass some information to tf then it is called Input Variable 
Output Variable : If we want tf to print a particular value in the output is called output variable
Ex: main.tf
Provider "aws"{
bunch of configuration 
}
resource "aws_instance" "Name of the resource" {
  ami = var.ami_id
  instance_type =  var.instance_type
}
but where will get the variables so what we need to do is before resource means in between provider and resource configuration what will try to is here we will write all the variables that we want to use.
Syntax for Variable creation:
Variable "instance_type" {
   description = "EC2 instance type"
   type = "string"
   default = "t2.micro"
  }
   variable "ami_id" {
      description = "EC2 AMI ID"
      type = "string"
  }
Lets say after EC2 instance creation we dont want to go to AWS UI an we dont want to check the Public IP. If our EC2 instance having public IP what we can do is in the output variable we can tell tf to print public IP, every time tf runs once the tf creates resource in aws as an output it will give oublic ip back.
Will create something called as main.tf, inside the main.tf as ususally will write the provider configuration or we can write the provider configuration in provider.tf as well. 
First we can start with key word called variable and after that we should be provide the name of the variable we want to use, inside that description is not mandate it just readable purpose. 
Any programming language when we are creating a variable if it is statically type programming langauge we will mention what is the type of the varaible. type=string it can be bullian or any other and the default value is t2.micro 
Whenever we use this particular variable using var.name of the variable (var.instance_type) it will replace with default t2.micro. what will happens is we are not hard coding the values we are using in a seperate variable section and we can update this variable section from the tf apply command as well that means we can pass the values to this variables from the tf apply command or we can out the values in a different tf file as well which is called tfvars.
what exactly we are trying to do using variable is we are paramatarise out tf project so that it is just not used by one particular team as a DevOPS member we can redistribute or reuse particular tf project to different team.
these are the input variable where we can pass the information to tf project. where as we can also use output variable but the syntax will be slightly different.
The syntax for the output variable will start with output keyword which we ask tf to give back once the tf apply command successful.
Output "Public_IP" {
  descriptio = "Public IP address of EC2 instance"
  Value = "aws_instance.example_instance.Public_IP"
  }
lets say we want to get the aws instance public ip so will say output public ip and there we can mention what is the value we are looking for.
resource.resource name
If we want for a different EC2 instance will say aws_instance.example_instance2 or the name of the particular resource and followed by the public IP because we are looking for public ip.
When we use output as a keyword we are telling tf to give me that particular information. when we are providing or prefexing with variable as keyword we are tellinig tf take this as values.
when we write tf project in ouranization there will be a structure for terraform because we cant run everything in single main.tf, what will do is we will split it.
The provider configuration from the main.tf can be writen in provider.tf file, input values we can pass they can be provided in the input.tf, the output variables can be provided in the output.tf, 

TF Structure:
main.tf
provider.tf
inpit.tf
output.tf
terraform.tfvars

this is the standard peocess, we can change the names of this file but if we use this standard way anybody who will read your project they will understand.
and the file name called main.tf apart from this there is a file calles terraform.tfvars
** terraform.tfvars **
when we are executing the particular tf project we want to take the values of the variable dynamically.  so the instance_type for one project the DevOps team is supporting is t2.micro and tomorrow someone comes and executing this they want the instance type to be t2.medium or other type.
how to completely paramaterize or how to pass this value to variable, in terraform there is a concept called tfvars
so tfvars what will try to do is will try to put the values to these variables that means we wrote the entire file we wrote input.tf, output.tf along with that we create a file called terraform.tfvars and inside this file we will write that aws_instance = "t2.micro" actual values of the varaibles.
the advantage of this is tomorrow any team tries to execute this entire project they can just change the tfvars file. 
Lets say we have a TF project for a Dev, Staging and Prod environments, we want user same tf project for different environments, for one environment tf script for EC2 instance and the tf instance type for the Dev environment is t2.medium where as for production environment the value is t2.micro then what will do inside input.tf will create that variable but inside terraform.tfvars will actually pass the values for it its just a key value pair file where inside that file will write values for each and every variable that we are creating in input.tf 
Lets say we want to write a value Instance type (Instance_type = "t2.micro") then key value pair (key name = "xxxx") security groups like subnet id's all of this thing we can provide in tfvars file and then we run terraform apply bydefault terraform look for terraform.tfvars file and it will replace or update the values inside input.tf, what ever we provde in input.tf
tfvars file bydefault will have terraform.tfvars if we want to change it dev.tfvars in such case what will do it we need to pass that information to terraform apply command
we will say what is the name of the tfvars if we are using terraform.tfvars we dont need to pass that to terraform apply but if we are changing the name then we need to pass that to terraform apply command.

** Conditional Expressions **
Conditional Expressions are nothing but, insome cases we want to excute, lets say there is a resource block and this particular resource block called aws_instance, in that particular resource we want to execute some values like 10 or 12 values want to execute on Dev environment where as if its a Prod aws environment we ant to modify these couple fields or dont want to execute couple of fields.
For example we have a S3 bucket and if we are creating S3 bucket on Dev cluster i.e. Dev aws environment, lets say we want to enable public access to S3 bucket, where as if it a Prod cluster we dont want to enable the public access to the S3 bucket. what we are trying to do here is we are going to porform Conditional actions. Other programming langueges we are handled bu If condition.
where as in tf we have something called as Conditional Operators, 
The syntax for conditional operator is 
Condition ? true_val : False_Val
Condition is an expression that evaluates either true or false
true_val is the value that is returned if the condition is true
false_val is the value that is returned if the condition is false

lets take the simple example
resource "aws_Security_group" "example" {
    name = "example_sg"
    description = "example security group"
    ingress {
    from_Port = 22
    to_port = 22
    protocal = "tcp"
    cidr_blocks = var.environment == "Production" ? [var.production_subnet_cidr] : [var.development_subnet_cidr]
    }
   } 
we are trying to create resurce calles security group in aws, we have provided the name of the security group and provided the description of the security group in the security group we are saying allow 22 which is allow 22 SSH but only allow for a particular cidr block that means allow SSH to this particular instance where the security group is assigned where if the environment is production then assign production cidr block if the environment is not production then assign dev cidr block.
var.production_subnet_cidr is
varable "Production_subnet_cidr" {
description = "CIDR blovk for production subnet"
type = "string"
default = "10.10.1.0\24"
}

varable "development_subnet_cidr" {
description = "CIDR blovk for development subnet"
type = "string"
default = "10.10.2.0\24"
}

** Built in Functions **
TF provides a wide range of buil in functions that we can use with in our configuration files to manipulate and tranform data. These functions help to perform various tasks when defining infrastructure.

## Day 3
Modules
We will write a complete reggular tf project and then we will convert that into a tf Module.
Module in Terraform -- > Age, Ownership, Maintenance
We are working in an organization and this Organization have some million of lines source code and lets say this source code written in Java and the name of the company is Amazon. we all know all companies these days are using micro service architecture.
at this moment assume amazon using Monolithic architecture which means all million of lines code is written in one single application or one single project. we might be thinking that everything is written as a single application then what is the problem, the problem would be there is a bug in this particular application and there is a new person who joined this team and we assigned to him with this particular bug, now this person would take Ages to understand where exactly the bug or that person may take lot of time to read firstly he entire millon lines of code.
Technically is not easy to find where the bug is so this person ends up spending lot of days to just understand where the bug is and second thing the lack of ownershi, again lets say there is a bug and we want to assign this particular bug to any of the developer and tell them that ok try to fix this bug because this is created due to the code or due to changes that we have implemented that would be not possible because there could be 100 of deveoplers writing millions of lines of code and we cant say exactly who owns the which part so there is lack of ownership.
Maintenence would be very very difficult, what does it mean lets say we want to keep upgrading this particular application. we want to make sure that this application dont want any security vulnerabilities so the problem is again because this is one signle application and have milliones of lines of code. It is practically to create lots of challange to maintain the application. So to address all of these things and beyond this there is another simple thing that is lets you figured out the bug as well and you try to fix this thing. now to test this piece of code which part of the application would we test.
because it is single application we will test the entire application and we will deploy the entire application so testing would also be very difficult.
To address all of these things what developers had done or what software industry has done is they have transition from monolithic architecture to micro service architecture same thing happens in TF as well.
Terraform: Even with TF there will be one particular provide that we want to automate, ususally these days companies mostly there will be one single provider. but other cases if we work on hybrid cloud architecture we might be work on multiple providers as well. 
Lets say that in your organization AWS and we are using TF to automate AWS, Lets asume we are using one particular TF Project and there can be hundreds of development projects. take example of one development team. Even for one dev team as a devops engineer we might create lot of resources. one single development team can use VPC, EC2 Instances, Load Balancer and they might be use EKS cluster and lamda functions, S3 buckets.
If we try to put all of these things in one single TF project, if we create one TF project for all the requirement of this development team. Our TF project will increase leaps & bounds 
















Q-1 How AWS\GCP\Azure is linked to Terraform --->Terraform integrates with AWS, GCP, and Azure through provider plugins, allowing you to manage infrastructure in these cloud environments. You write configuration files, define the desired state of resources, and then use Terraform commands to create, update, and manage those resources across various cloud platforms. The flexibility of Terraform in supporting multiple providers enables seamless multi-cloud and hybrid cloud management.

Q-2 What are the different providers TF support ---> Categorized to Official (aws,azure,gcp,kubernities), partner  , community

Q-3 How many Providers can be deployed in single code ---> There is no fixed limit to the number of providers you can use in a single Terraform configuration. You can deploy resources across different cloud providers like AWS, Azure, GCP, and others, using multiple provider blocks, optionally with aliases to manage different accounts, regions, or subscriptions. However, when working with multiple providers, always ensure that the configuration and state management are handled appropriately for the complexity of your infrastructure.


TASK -- Tearraform Cheek codes --- need to verify 10 codes

Q-4 Can we deploy 2 VM's in 2 diffetrent regions at a time in a single code --> yes we can create 

Q-5 How to destroy a single instance --> using terraform destroy -target command we can delete single instance

Q-6 What is the difference b\w input and output variable  --> If we want to pass some info to tf then its called input variables, if we want tf to print some value is called outpout variables

Q-7 How many keys we can generate a day

Q-8 Explain complete life cycle of Terraform
Terraform init
Terraform plan
Terraform apply
Terraform destroy


