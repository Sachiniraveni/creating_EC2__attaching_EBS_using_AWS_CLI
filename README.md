<h2>Spinning Up the EC2 insances using AWS_CLI</h2>

<b>Objective:-</b> 

Create a key pair <p>
 🔅Create a security group<p>
🔅Launch an instance using the above created key pair and security group.<p>
🔅Create an EBS volume of 1 GB.<p>
🔅The final step is to attach the above created EBS volume to the instance you created in the previous steps.<p>


<b>SOLUTION:-</b>

Step 1:  You need to install the AWS CLI for your operating system.  In my case I'm using Windows so I have installed the .msi installer.
 AWS-CLI download link = https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-windows.html
 
#aws version (run this command to check whether the installed is successfull)

So, now lets begin with execution.

Step 1: -  We will be using IAM user to login. so, go ahead into ur AWS account and create an IAM user and download the Access key ans secret access key.
Make sure not to share the ID and key with any one.

Step2:- Open the terminal(if your using linux or MacOs and CMD for wwindows user).

Step3: - Our first objective is too login with the IAM user so type the below command.<p>
<b>#aws configre</b>
and enter your credentials on prompt, as shown in below picture.
![Screenshot (922)_LI](https://user-images.githubusercontent.com/46579657/97539153-7ec65900-19e7-11eb-8fc3-34354b6c93f5.jpg)

To launch an EC2 instance we need  a key pair and to create that using cli we can always take help  of the (#aws ec2 help) command. as shown in the above picture.

Step 4:-So the command to create a key-pair is,
#aws ec2 create-key-pair --key-name CLIKEY  (CLIKEY is the name of the  key-pair. You can give any name to it). As shown in the below picture.
![Screenshot (923)](https://user-images.githubusercontent.com/46579657/97539955-e335e800-19e8-11eb-9d32-bede15023f0f.png)

And go to the your AWS Account, go to the key-pair section and refresh it. You will be able to see the recently created key-pair in the panel. Just like the below pic.
![Screenshot (924)_LI](https://user-images.githubusercontent.com/46579657/97540391-943c8280-19e9-11eb-9850-d976be87083e.jpg)

 
 




Step 5: - Create a security Group
command to create a security group is,
# aws ec2 create-security-group --group-name sgcli --description "group created"
Where, sgcli -  is the name of the group. You can give any name.
       Group created -  is the comment or a description.
as shown in the below picture.

`![Screenshot (925)](https://user-images.githubusercontent.com/46579657/97542150-41b09580-19ec-11eb-9db0-897b9165d02b.png)

![Screenshot (926)](https://user-images.githubusercontent.com/46579657/97542328-905e2f80-19ec-11eb-96a9-33df2683acaa.png)

As you can see in the above picture that our security group has been updated and is attached to the default VPC.

Step 6:- Creating inbound rules.
Command for the same is,
#aws ec2 authorize-security-group-ingress --group-id "urgroup_id" --protocol tcp --port 22 --cidr 0.0.0.0/0
urgroup_id - is the security group id, wwhich was created in the previous command.

![Screenshot (928)](https://user-images.githubusercontent.com/46579657/97542905-8557cf00-19ed-11eb-8bd4-8f734638da37.png)

and go to aws account and refresh the panel, it will be created.

![Screenshot (931)](https://user-images.githubusercontent.com/46579657/97543147-d1a30f00-19ed-11eb-96e6-502c07b8045b.png)

step 7 :- Run ec2 command

![Screenshot (932)_LI](https://user-images.githubusercontent.com/46579657/97543568-6c035280-19ee-11eb-845e-845eea7d4e95.jpg)

 AMi-id =  I have choosen the amazon linux<p>
 instance-type = I am using the free tier instance, t2.micro.<p>
 subnet-id = can be found from the region you are launching. Easlity available on the internet and the offcial docummentation of the AWS.<p>
 security groups, are the same which we have created earlier.
 
 So, after this command you will be able to launch an instance in AWS cloud.
 
 As, you can see in the below picture, I have launched an instance using the above mentioned steps and the instances is up and in running state.
 
 ![Screenshot (933)](https://user-images.githubusercontent.com/46579657/97544560-cd77f100-19ef-11eb-8477-585d5bb9ec3a.png)
 
 
Step 8 :- creating an EBS volume using command line

![Screenshot (935)](https://user-images.githubusercontent.com/46579657/97545240-b4bc0b00-19f0-11eb-9459-131536036e18.png)

Step 9 :-  Attaching the volume which is created in the step 8.

![Screenshot (937)](https://user-images.githubusercontent.com/46579657/97545362-e7660380-19f0-11eb-891d-ce3d7cef9203.png)

after running this both the commands you should be able to create and attach the EBS volume to your running instance.

![Screenshot (936)](https://user-images.githubusercontent.com/46579657/97545669-580d2000-19f1-11eb-99cf-f0c3cfd21a16.png)

As shown in the above picture, we can conclude that my volume is been attached to the instance and we are now good to go.

THANK YOU for taking your valuable time to read this. 
If you found this interesting and new then please share it with your peers.







.







  
