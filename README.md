# Creating-and-Configuring-CloudWatch-Alarms 
<h2>Description</h2>
<br/> In this demo we will create and configure an alert in CloudWatch to monitor a EC2 instance 
<br />
<br/> <br/>
<img src="https://github.com/user-attachments/assets/2268ab00-acdb-457f-9edc-986dcac9a89e"/>


<h2>Languages and Utilities Used</h2>

AWS Services: SNS, CloudWatch, EC2 

<h2>Environments Used </h2>

- <b>AWS console </b>

<h2>Project walk-through:</h2>
<br/>
<p align="center">


### **Prerequisites**  
- Have an [AWS account](https://aws.amazon.com/console/).   
- Have a valid email address that can verify SNS.



## Step 1: Register a valid email for SNS

<br/> Navigate to the SNS (Simple Notification Service) from the AWS console and enter a valid email address. We will use this email address to receieve our CloudWatch alarm later in this demo <br/> 

<br/> Select standard and enter a name <br/>
<img src="https://github.com/user-attachments/assets/7aaf3fe9-cd97-4a96-b158-19d547abfe42"/>
<br/> Next select create topic and next select create subscription. Enter a valid email address and select create <br/>
<img src="https://github.com/user-attachments/assets/9c49ee83-c3ef-4c01-b94c-0cabec572926"/>
<img src="https://github.com/user-attachments/assets/2f7f69bd-97ac-4ea2-b451-daafbc901c5d"/>
<br/> Now confirm and validate the subcription at the registered email endpoint <br/>
<img src="https://github.com/user-attachments/assets/cd692806-c1d7-466b-89b9-b78d8abcab6c"/>
<img src="https://github.com/user-attachments/assets/edd0a2f5-63ea-4ff7-8b61-d0aadbd61864"/>
<img src="https://github.com/user-attachments/assets/60648dfb-6873-4ce0-a1a4-12a23b0505d7"/>
<img src="https://github.com/user-attachments/assets/5405802b-3ea5-40f6-a944-212c18d09491"/>

 ##  Step 2: Create an EC2 instance

<br/> From the console navigate to EC2 instances, select launch instance, name the instance and select proceed without key pair (for DEMO purposes only). Leave the rest as default and click on "Launch instance now" <br/>

<img src="https://github.com/user-attachments/assets/30d79de1-a760-4e4b-9837-027e55357864"/>
<img src="https://github.com/user-attachments/assets/9924475c-a8b5-462e-bada-232fd7a5036f"/>
<img src="https://github.com/user-attachments/assets/637afb5f-19de-49af-9667-89d2bc1b6815"/>


## Step 3: Connect to the EC2 instance 

<br/> Once the instance is in the running state click on connect 2x to connect to the instance from the browser <br/>

<img src="https://github.com/user-attachments/assets/c2734f95-913c-4fd4-8be8-1b541dbd7d00"/>
<img src="https://github.com/user-attachments/assets/36a75324-51e9-415a-98de-4440b307daa6"/>

<br/> Now become root and install the stress command. We will use this command to stress test our EC2 instance to manipulate cpu usage and other metrics <br/>

```Bash
sudo -i
dnf install stress -y
```

<img src="https://github.com/user-attachments/assets/15b811d8-2ef5-41d3-9eaf-df1847364d89"/>

<br/> Now run the following command to simulate system load by stressing 4 CPU cores, 4 I/O operations, allocating 1GB of memory in virtual memory, and writing to 2 HDD files. <br/>

```Bash
stress --cpu 4 --io 4 --vm-bytes 1G --hdd 2
```

<img src="https://github.com/user-attachments/assets/87aa3c1b-d07e-41ab-a35c-55bb4ad2d9b4"/>
<br/> Confirm metrics are available in the monitoring section <br/>
<img src="https://github.com/user-attachments/assets/578d92dc-fa60-4b86-9cbf-023e8f5d7f47"/>

## Step 4: Create a CloudWatch alarm

<br/> Navigate to CloudWatch from the console and select create alarm <br/>

<img src="https://github.com/user-attachments/assets/d7a77102-5fad-4e2b-b732-41b233ec7475"/>
<br/> Next click select metric and copy and paste the EC2 instance ID to view available metrics <br/>
<img src="https://github.com/user-attachments/assets/1a023c57-9606-43ef-9c96-2dd26237ac5d"/>
<img src="https://github.com/user-attachments/assets/87468378-20a9-4188-8162-17df1886b165"/>
<br/> From the list of options select cpu utilization <br/>
<img src="https://github.com/user-attachments/assets/5089c4aa-5e01-4d87-8de2-cda403979609"/>
<br/> Next at the Specify metric and conditions screen leave as static and define the threshold value <br/>

<img src="https://github.com/user-attachments/assets/9673ffe4-abe9-4190-a1eb-64d6c4081682"/>
<br/> Since the threshold has been exceeded for the alarm it is visible and we should get notified from our SNS email that we configured earlier once the alarm has been created <br/>
<img src="https://github.com/user-attachments/assets/802c1248-33b8-4f5f-baa6-45e5bea1c69c"/>
<br/> Next select next and choose select an existing SNS topic to pick the one made earlier <br/>
<img src="https://github.com/user-attachments/assets/a608b7d3-be0d-4331-8af6-019818a21d8e"/>
<br/> Click next and configure the alarm name and description for the endpoint <br/> 
<img src="https://github.com/user-attachments/assets/67bf777f-3ffa-4dfe-9c65-f4515f93c9a8"/>
<br/> Preview the message <br/>
<img src="https://github.com/user-attachments/assets/0bfe86cc-5aaf-4148-a0e1-291c0a809ea7"/>
<br/> Now click next, confirm configurations, and create alarm. (Note: the alarm states insufficent data because it has just been created) <br/>
<img src="https://github.com/user-attachments/assets/c26818cf-ac26-4105-8ed8-c9da82645f35"/>

## Step 5: Confirm alarm is working via SNS endpoint

<br/> Since the CPU utilization threshold was exceeded from the stress command the the alarm should notify the SNS email endpoint with the message chosen. Navigate to the SNS email you entered and confirm <br/>

<img src="https://github.com/user-attachments/assets/bf6e63de-9002-4d7a-86db-85bf2990adc1"/>
<br/> The alarm is working properly. Now view in console and confirm in <br/>
<img src="https://github.com/user-attachments/assets/444436de-95b4-44df-b7de-b33673370798"/>


## Step 6: Kill the stress command 

<br/> To test our CloudWatch alarm further go to the EC2 instance terminal and pres ctrl c to kill the stress command. Aferwards the alarm status should no longer state in alarm  <br/>

<img src="https://github.com/user-attachments/assets/309a0c49-7605-4803-9152-e8fbef4b32ac"/>
<br/> Now we can see that the state is OK <br/>
<img src="https://github.com/user-attachments/assets/80c7f6e8-81ce-4a11-a772-9038b0c96fd4"/>
<br/> Note: we will not recieved an email now that the cpu utilization has returned within the threashold because the alarm was set for if the condition of 85% cpu util has been reached to notify the SNS endpoint <br/>
<br/> In summary we successfully created an EC2 instance, installed the stress package on the instance and ran it to mock cpu utilization, we configured a CloudWatch alarm and sucessfully tested the SNS endpoint. <br/> 

<img src=""/>
<img src=""/>
<img src=""/>


<img src=""/>
<img src=""/>
<img src=""/>
<img src=""/>

## Step

<br/> <br/>

<img src=""/>
<img src=""/>
<img src=""/>
<img src=""/>
<img src=""/>

## Step

<br/> <br/>

<img src=""/>
<img src=""/>
<img src=""/>
<img src=""/>
<img src=""/>

## Step

<br/> <br/>

<img src=""/>
<img src=""/>
<img src=""/>
<img src=""/>
<img src=""/>
