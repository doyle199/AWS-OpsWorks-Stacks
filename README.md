# AWS-OpsWorks-Stacks
AWS OpsWorks Stacks

First, one must create a basic application server stack. From the AWS Management Console go to AWS OpsWorks Stacks. Click on stacks in the left menu. Click on Ass stack on the right side.

![alt text](https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/add_stack.png)

Choose Chef 12 stack. Create a stack name. Choose the correct region. Choose the correct Operating System. Leave Use custom chef cookbooks as no for now. That will be changed later. Click Add Stack.

![alt text](https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/stack1.png)

![alt text](https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/stack2.png)

![alt text](https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/stack3.png)

![alt text](https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/stack4.png)

To authorize RDP access, first go to the AWS EC2 console. Scroll down to Security Groups in the left menu and click on it.

![alt text](https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/scroll.png)

Check the AWS-OpsWorks-RDP-Server box.

![alt text](https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/SG_1.png)

Scroll down and click on inbound rules. Click edit inbound rules.

![alt text](https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/rules.png)

Click Add rule. Choose RDP for Type. Enter the correct source or enter 0.0.0.0/0. Click Save rules.

![alt text](https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/rules_1.png)

![alt text](https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/rules_2.png)

To authorize RDP for a user, go to AWS OpsWorks Stacks. Choose your stack. 

![alt text](https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/works.png)

Click on Permissions in the left menu.

![alt text](https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/per.png)

Click on edit near the bottom right of the page. Check the box for SSH/RDP and any other permission you would like to grant that user.	Click Save.

![alt text](https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/per_2.png)

To create a custom cookbook go to your computers desktop or desired folder destination. Create a folder called “iis-cookbook” on the desktop. Inside the “iis-cookbook” folder create a metadata.rb file with the following details: 

name "iis-cookbook"

"version "0.1.0"

![alt text](https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/meta1.png)

Inside the “iis-cookbook” folder also create a folder named “recipes”. Inside the recipes folder create a folder called “deploy.rb” with the following details: https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/template1.txt

![alt text](https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/recipes.png)

Inside the “recipes” folder create a folder called “install.rb” with the following details: https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/template2.txt

![alt text](https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/rec_2.png)

Create a zip file of the entire “iis-cookbook” folder. Create another folder called “iis-application” on the desktop. Create a file called “default.txt”. Add the following to the file with TextEdit or similar program and put your name where it says “YOUR NAME”: https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/Template3.mdoc

![alt text](https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/default.png)

Change the file name from “default.txt” to “default.htm”. Navigate to AWS S3. Click create bucket on the right side.

![alt text](https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/bucket.png)

Create a Bucket name and select the appropriate region.

![alt text](https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/bucket2.png)

![alt text](https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/bucket3.png)

Choose the S3 bucket you created.

![alt text](https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/bucket4.png)

Upload the “iis-cookbook.zip” and “default.htm” files you created on your computer. Remember: the “default.htm” is in the folder called “iis-application”.

![alt text](https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/bucket5.png)
