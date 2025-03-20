
- All the resources are created through AWS UI using root account/IAM.
- The primary work of DevOps engineers is to do infrastructure management/automation. But this UI is not automation friendly as through UI for any task we end up creating resources consuming more time. Using UI is good until we get less requests for rescource creation. But to act on many requests at a time, automation is needed.
- This problem is common across various tools not only AWS. So AWS comes up with its own APIs (Application Programming Interfaces). Using it we can automate creating, deleting, managing resources on AWS
  - e.g:- To create 10 EC2, using APIs of AWS we can write shell scripts and invoke the API and send the request programatically(not manual)
  - Using API we programmatically reach that app passing credentials, tokens or any other required things.  These programs can be scripts, python code, etc.
  - Tools to automate AWS infrastructure :- CLI, terraform, AWS CFT, AWS CDK 
  - Here apart from CLI, rest tools are IaC tools
 
# AWS Commad Line Interface

- AWS CLI is python utility/program written by AWS engineers using which we can pass some arguments to it (credentials, variables) and create resources on AWS
- For any app, there are 2 ways to connect :- UI and API (Programmatical)
  - e.g: To create S3 bucket using api.aws.com/s3/create
  - AWS writes API to create S3 bucket. Write specific URL in program passing required parameters like S3 name, versioning for S3 then call API and pass arguments to python code and S3 gets created. So we reach apps not thro UI but thro program. Program can be of our choice. Application owner will tell us if we want to create resources, reach out to API we created and use HTTP method declared and pass parameters to get resource in JSON or any format.
 
- But as DevOps engineer, we dont tend to write programs, so CLI, CFT, Terraform create abstraction layer. So using abstraction layer, no need of writing all these things.
- If CLI created python app for us, we have to install it and call using AWS along with parameters(./aws/s3) along with name, versioning. Then AWS CLI will convert to API call and send to AWS
- So as DevOps engineers, we dont need to know about API, calling API, writing program. Instead we need to know how to install CLI  and use it by passing parameters. Using it we can automate any resources with AWS.. This writing parameters is like writing text.

- AWS CLIS is an interface between user and API
- To invoke AWS CLI :- **aws $parameters** and submit
  - This will translate request into an API call AWS understand and AWS creates resources for us
  - AWS CLI is very quick entering commands, in CFT and terraform we need to write yaml files
 
- CLI is preferred if we need quick output of anything.
  - Suppose we need to get list fo S3 buckets :- **aws s3 ls**
  - Whereas in CFT and terraform we need to write yml files and execute them
  - But if we need to create large infrastructure or stack of resources on AWS,then CFT and terraform is used as they follow API as a code which helps in reviewing code and other things
  
-------------------------------------------------------------------------------------

Practical Demo
-
- Download AWS CLI from AWS CLI documentation.
- Pre-requisite is to install python on our machine
- To check aws cli :- **aws --version**

- To configure AWS CLI on our machine to talk to AWS account :- aws configure
  - It asks for "Access Key ID", "Secret Access Key", "AWS region", "Output Format". Provide to configure the account
- For any API to access, there are access keys, API tokens. In AWS we use access keys as they're similar to our username and password for UI login.

- To get access keys :- Login using IAM user Account - Security credentials - Access keys
  - To create access key - Create access key - Get details of access and secret key

![image](https://github.com/user-attachments/assets/edeef554-7188-47a4-859c-14db7e7b0360)

- After getting the keys only configure aws account using CLI

- We can check the configuration is done using running any command :- **aws s3 ls**
  - This command understands AWS CLI wants to talk to S3 service in account and invoke "ls" command.
  - AWS CLI will translate the command to API call which AWS understands. Then making API call, we get output
 
- To create EC2, we need to pass parameters like name of EC2, distribution AMI(OS), instance type, key-value pair. This info has to be passed through CLI as well
  - Command :- aws ec2 run-instances \
    --image-id ami-0abcdef1234567890 \
    --instance-type t2.micro \
    --key-name MyKeyPair \
    --security-group-ids sg-0123456789abcdef0 \
    --subnet-id subnet-0123456789abcdef0 \
    --count 1 \
    --tag-specifications 'ResourceType=instance,Tags=[{Key=Name,Value=MyEC2Instance}]'

--image-id → AMI ID (e.g., Amazon Linux 2, Ubuntu, etc.)
--instance-type → Instance type (e.g., t2.micro)
--key-name → Key pair name for SSH access
--security-group-ids → Security group for inbound/outbound rules
--subnet-id → Subnet ID for VPC placement
--count → Number of instances to launch
--tag-specifications → Add tags for identification

- After creation, we can see output in JSON format as selected earlier while configuring.

