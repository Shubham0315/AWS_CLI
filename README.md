# AWS_CLI

- All the resources are created through AWS UI using root account/IAM.
- The primary work of DevOps engineers is to do infrastructure management/automation. But this UI is not automation friendly as through UI for any task we end up creating resources consuming more time. Using UI is good until we get less requests for rescource creation. But to act on many requests at a time, automation is needed.
- This problem is common across various tools not only AWS. So AWS comes up with its own APIs (Application Programming Interfaces). Using it we can automate creating, deleting, managing resources on AWS
  - e.g:- To create 10 EC2, using APIs of AWS we can write shell scripts and invoke the API and send the request programatically(not manual)
  - Using API we programmatically reach that app passing credentials, tokens or any other required things.  These programs can be scripts, python code, etc.
  - Tools to automate AWS infrastructure :- CLI, terraform, AWS CFT, AWS CDK 
  - Here apart from CLI, rest tools are IaC tools
