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

## Step 4: 

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
