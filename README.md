# AWS CloudWatch Monitoring
![image](https://user-images.githubusercontent.com/88166874/132838647-78873ea4-51c1-410a-95cf-8bc5ca1cc5f7.png)  
Cloudwatch is a monitoring service for AWS resources and services. It helps you make your services scalable and highly available. It can track metrics, collect log files, and automatically react to changes, all depending on how you configure it.  
## Auto Scaling and Load Balancing
CloudWatch can be used to set up an alarm to launch an auto scaling group. Auto scaling automatically adjusts the amount of computational resources based on the server load.  
Load balancing distributes traffic between EC2 instances so that no one instance gets overwhelmed. For example, if the CPU reaches a certain percentage, such as 50%, load balancing can scale out to distribute traffic between EC2 instances.  
## EC2 Simple Notification Service (SNS)
EC2 SNS is a notification service that can send an email or text message whenever CloudWatch detects activity.  
