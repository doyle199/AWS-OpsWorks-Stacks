# AWS-OpsWorks-Stacks
AWS OpsWorks Stacks

First, one must create a basic application server stack. From the AWS Management Console go to AWS OpsWorks Stacks. Click on stacks in the left menu. Click on Add stack on the right side.

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

![alt text](https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/bucket6.png)

Click on the “iis-cookbook.zip”.

![alt text](https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/cookbook.png)

Click on the “Make public” button near the top. Make a record of the S3 Object URL at the bottom. It will be needed to connect to OpsWorks Stacks.

![alt text](https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/zip.png)

Click on the Permissions tab. Click on Bucket Policy.Enter the following in the editor and make sure the correct bucket name is put where it says “YOUR-BUCKET-NAME”: https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/template3.jscsrc

Click save.

![alt text](https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/pub.png)

Navigate to the AWS OpsWorks Stacks created earlier. Click on Layers in the left menu. Click on add layer at the bottom right of the page. Give it a name and a short name. Select a security group if necessary. Click Add Layer.

![alt text](https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/layer.png)

To enable custom cookbooks for the stack, go to the main page of the OpsWorks Stack you’ve been working with click on Stack Settings on the right of the page.

![alt text](https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/run.png)

Check the box so it says Yes next to Use custom Chef cookbooks. Choose “S3 Archive” for Repository type. Copy and paste the S3 cookbook object URL from earlier for Repository URL. Click Save.

![alt text](https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/ore.png)

To assign the recipe to a lifecycle event, on the main page go to Layers in the left menu. Click on Recipes.

![alt text](https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/recipes_4.png)

In the Setup box type “iis-cookbook::install”. In the Deploy box type “iis-cookbook::deploy”. Then choose the plus symbol to add the recipes to the layer.	Click Save.

![alt text](https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/Save_2.png)

Click Add instance on the right side of the layer.

![alt text](https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/ad_in.png)

Create a hostname.	Choose the correct instance size.	Choose a subnet.	In Advanced make sure its 24/7.	Click Add Instance.

Click start.

![alt text](https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/start.png)

Create another instance in a different availability zone to be used with a load balancer later.

![alt text](https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/online.png)

If you did not deploy the instances with working lifecycle events you can do the following: Click on Stack in the left menu, Click on Run Command. 

Choose the dropdown Update Custom Cookbooks next to Command. Click on Update Custom Cookbook.

![alt text](https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/update.png)

After the update finishes run the execute recipes command. Make sure the correct instances are selected.

![alt text](https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/success.png)

To check if the IIS is installed and running sign into AWS with the user that you assigned RDP access to. Go to your OpsWorks stack. Click on instances. Choose an instance you installed the custom cookbook recipe to. Click on RDP in the upper right. Set session to two hours. Click on generate password.

![alt text](https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/generate.png)

Take note of the password, the instance’s public DNS name and username. You may need them.	Click on Download an RDP file. Click Acknowledge and close.

![alt text](https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/ack.png)

Click on the RDP file you downloaded. You may need to download Window Remote Desktop first.	Enter the password.	Go to the C drive.	You should see a folder named “inetpub”.

![alt text](https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/inetpub.png)

Go to Control Panel > Administrative Tools > Services.	Scroll to the bottom.	You should see a service called “World Wide Web Publishing Service” and it should have a status of “Running”.

![alt text](https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/running.png)

If you see the two things mentioned above, it is working correctly. Next, to deploy an app sign back in as the root user and go back to your OpsWorks stack. Click on Apps in the left menu. Click on Add app.

![alt text](https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/add_app.png)

Name the App. Change Repository Type to Other. Add the following Environment Variables with your relevant information:

S3REGION us-west-2

BUCKET cca640p2

FILENAME default.htm

Click Add App.

![alt text](https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/add_app2.png)

![alt text](https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/add_app3.png)

Click deploy on the right side.

![alt text](https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/deploy.png)

Click Deploy.

![alt text](https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/deploy2.png)

![alt text](https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/deploy3.png)

Click into the instance. Click on the DNS link. You should see a webpage with your name on it.

![alt text](https://github.com/doyle199/AWS-OpsWorks-Stacks/blob/master/hello.png)






