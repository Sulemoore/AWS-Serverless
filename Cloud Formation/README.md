# Creating, Modifying Templates, and Updating Stacks
The goal of this lab is to show the steps in creating stacks, modifying templates, and properly updating stacks using change sets in the AWS Management Console. To work on this lab, you need to have a good understanding of concepts like templates, stacks, change sets, security groups, EC2 instances, and networking resources in AWS.
## SCENARIO
For this lab exercise, you need to create the following cloud environment setup. 
1. You will start by creating a key pair. The key pair will be used by CloudFormation when deploying EC2 instances. 
2. Create a stack using the CloudFormation template provided in `code`. 
3. Once you are done with the initial setup, you will modify the template based on the requirements detailed in the instructions. 
4. Update the existing stack using change sets taking note of how your template changes affect your resources.
## Cost
This lab will not cost you as it falls within the free tier. Stack will also be deleted afterwards.
## Time
This lab will take approximately 20 mins. to complete.
## INITIAL SETUP
1. Create a key pair in the AWS Management Console.
<img width="905" alt="Screenshot 2023-01-19 at 12 15 01 AM" src="https://user-images.githubusercontent.com/101164153/213369822-000f1391-1a28-4545-a06c-203827858620.png">
2. Download the template in the `code` on your local machine and create a stack by uploading this file.
