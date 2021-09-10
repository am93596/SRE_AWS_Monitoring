# AWS CloudWatch Monitoring
![image](https://user-images.githubusercontent.com/88166874/132838647-78873ea4-51c1-410a-95cf-8bc5ca1cc5f7.png)  
Cloudwatch is a monitoring service for AWS resources and services. It helps you make your services scalable and highly available. It can track metrics, collect log files, and automatically react to changes, all depending on how you configure it.  
## Auto Scaling And Load Balancing
CloudWatch can be used to set up an alarm to launch an auto scaling group. Auto scaling automatically adjusts the amount of computational resources based on the server load.  
Load balancing distributes traffic between EC2 instances so that no one instance gets overwhelmed. For example, if the CPU reaches a certain percentage, such as 50%, load balancing can scale out to distribute traffic between EC2 instances.  
## EC2 Simple Notification Service (SNS)
EC2 SNS is a notification service that can send an email or text message whenever CloudWatch detects activity.  
# Setting Up Auto Scaling And Load Balancer  
## Create A Launch Template From An EC2 Instance
1. In AWS EC2 Console, click `Instances`. Select the instance you want to be used for the launch template. Then select `Actions` -> `Images and templates` -> `Create template from instance`. Enter the name and description for your launch template (e.g. `sre_amy_launch_instance_app`)
2. Click the checkbox under `Auto Scaling guidance`.
3. Most of the rest of the details will be automatically filled in. In `Network settings`, select `VPC`, and select the security group for your instance. Some of the input boxes in `Advanced details` may be red, with recommendations for what to enter; follow those recommendations, then click `Create launch template`.
## Create Auto Scaling Group With Load Balancer
