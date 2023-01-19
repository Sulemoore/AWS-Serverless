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
1. Create a key pair in the AWS Management Console.Makesure key pair name matches what is indicated in template or update template accordingly.
<img width="905" alt="Screenshot 2023-01-19 at 12 15 01 AM" src="https://user-images.githubusercontent.com/101164153/213369822-000f1391-1a28-4545-a06c-203827858620.png">

2. Download the template in the code on your local machine and create a stack by uploading this file.
3. Go to the CloudFormation page, create a stack by uploading the template file. 
4. Upload downloaded template. {CloudFormation automatically creates an S3 URL where the template will be stored once uploaded.}<img width="1699" alt="Screenshot 2023-01-19 at 12 34 02 AM" src="https://user-images.githubusercontent.com/101164153/213372216-77d1e863-1335-43e9-a433-5059c996190c.png">

5. Name the stack `td-lab-cf-simple-stack`. No need to set the parameters since the default values declared on the template are correct already.
6. <img width="1172" alt="Screenshot 2023-01-19 at 12 36 10 AM" src="https://user-images.githubusercontent.com/101164153/213372661-af8a791e-fb45-495f-8696-3cd911a03eea.png">

7. Continue on the next steps by clicking Next and then click Create Stack.
8. Once done, you should be able to see CREATE_COMPLETE status on your stack.
<img width="1153" alt="Screenshot 2023-01-19 at 12 45 38 AM" src="https://user-images.githubusercontent.com/101164153/213374310-09ebb416-6545-4d87-bfab-1ecc461f14b4.png">

