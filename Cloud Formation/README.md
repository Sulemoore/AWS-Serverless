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

2. Download the template in the code on your local machine and create a stack by uploading this file.<img width="709" alt="Screenshot 2023-01-19 at 9 29 37 PM" src="https://user-images.githubusercontent.com/101164153/213611742-24820fce-0f76-43cb-8093-7ede091b5205.png"><img width="716" alt="Screenshot 2023-01-19 at 9 30 23 PM" src="https://user-images.githubusercontent.com/101164153/213611807-9233b606-8d4e-46cd-a676-894f09aa8b4a.png">


3. Go to the CloudFormation page, create a stack by uploading the template file. 
4. Upload downloaded template. {CloudFormation automatically creates an S3 URL where the template will be stored once uploaded.}<img width="1699" alt="Screenshot 2023-01-19 at 12 34 02 AM" src="https://user-images.githubusercontent.com/101164153/213372216-77d1e863-1335-43e9-a433-5059c996190c.png">

5. Name the stack `td-lab-cf-simple-stack`. No need to set the parameters since the default values declared on the template are correct already.
6. <img width="1172" alt="Screenshot 2023-01-19 at 12 36 10 AM" src="https://user-images.githubusercontent.com/101164153/213372661-af8a791e-fb45-495f-8696-3cd911a03eea.png">

7. Continue on the next steps by clicking Next and then click Create Stack.
8. Once done, you should be able to see CREATE_COMPLETE status on your stack.
<img width="1153" alt="Screenshot 2023-01-19 at 12 45 38 AM" src="https://user-images.githubusercontent.com/101164153/213374310-09ebb416-6545-4d87-bfab-1ecc461f14b4.png">

## INSTRUCTIONS
1. Add an inbound rule on the `ProdSecurityGroup` to allow `SSH` traffic coming from `169.232.1.18`.
2. <img width="890" alt="Screenshot 2023-01-19 at 9 12 42 PM" src="https://user-images.githubusercontent.com/101164153/213610486-c9d69756-5f68-4455-95f8-0d756a3ed8f0.png">
3. <img width="806" alt="Screenshot 2023-01-19 at 9 14 20 PM" src="https://user-images.githubusercontent.com/101164153/213610575-f342ada5-dc64-4633-b4cd-07db3f2e9e73.png">

4. Create an Output to export the resource ID of the `ProdEC2Instance` to allow cross-stack references.
5. Add this code after the Resources section to export the instance ID of the `ProdEC2Instance`. The Value property returns the ID of the referenced instance, in this case, the `ProdEC2Instance`.
6. `Outputs:
  ProdInstanceID:
    Description: "Production instance ID."
    Value: !Ref ProdEC2Instance
    Export:
      Name: 'ProdEc2Instance'`
 <img width="716" alt="Screenshot 2023-01-19 at 9 30 23 PM" src="https://user-images.githubusercontent.com/101164153/213611847-afc805d1-4015-4850-993b-97f2995c6da7.png">
     
7. Change the instance type of the `DevEC2Instance` from `t3.micro` to `t3.small`.
To modify the instance type of the DevEC2Instance, you need to look for the InstanceType property.
You will notice that the InstanceTypeproperty is referencing a DevInstanceTypeParam parameter. This means we can change the value of the instance type using the paramter.
But, we don’t need to replace the value of the parameter in the template itself. CloudFormation allows you to change the values of a parameter via the AWS Management console when you create a change set. So, we will create a change set first then modify the parameter during that process.
1. Select the td-lab-cf-simple-stack. Select Stack Actions and click Create change set for current stack in the dropdown.Upload the modified YAML template.
<img width="1720" alt="Screenshot 2023-01-19 at 9 39 03 PM" src="https://user-images.githubusercontent.com/101164153/213612683-05eb9685-53e2-49df-9e4e-4c4665267b70.png">
<img width="1039" alt="Screenshot 2023-01-19 at 9 42 07 PM" src="https://user-images.githubusercontent.com/101164153/213612959-b7e37d76-7f44-4bc5-84f5-68723c654bbd.png">

9. Update the stack by using a change set and name it `td-lab-cf-v-0-1`. Once you verify the resources that will be affected by the changes you created on the template, execute the change set.
