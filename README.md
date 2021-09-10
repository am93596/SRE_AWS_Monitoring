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
3. Most of the rest of the details will be automatically filled in.  
4. In `Network settings`, select `VPC`, and select the security group for your instance.  
5. In `Network interfaces`, select `Remove`
6. Some of the input boxes in `Advanced details` may be red, with recommendations for what to enter; follow those recommendations, then click `Create launch template`.
## Create Auto Scaling Group With Load Balancer  
1. On the launch template confirmation page, click `Create Auto Scaling Group`.  
2. Enter the name for your Auto Scaling group (e.g. `sre-amy-auto-scaling-group`).  
3. Leave `Launch Template` details as default, and click `Next`.  
4. Leave `Instance purchase options` as `Adhere to launch template`.  
5. In `Network`, select the subnet that your instance is operating in, then click `Next`.  
### Adding the Load Balancer  
6. Select `Attach to a new load balancer`, and set the type to `Application load balancer`.  
7. Name the load balancer - don't use underscores in the name (e.g. sre-amy-load-balancer-demo-1).  
8. Set `Load balancer scheme` to `Internet-facing`, and select at least a second Availability Zone
9. In `Listeners and routing`, select `Create a target group`. Tick the box for `ELB`, and `Enable group metrics collection within CloudWatch`. Click `Next`.  
10. `Desired capacity`: `1`; `Minimum capacity`: `1`; `Maximum capacity`: `3`.  
11. `Scaling policies`: Set to `Target tracking scaling policy`. Name it, set the `Metric type` to `CPU`, and set the `Target value` to `50`. Click `Next`, then click `Next` again on the next 2 pages.  
12. Click `Create auto scaling group`.  
## Target Group Configuration  
