# Travel Memory Deployment
## Introduction:
  Travel memory application is developed on MERN stack. this project will explain on how to deployit on AWS with load balancer using cloudflare for DNS setup.
## Deployment steps:
### 1. Create EC2 instances:
  - To deploy the application we need instance. As the ELB is used for load balancing we are creating two instances named as pk-tm-0 and pk-tm-1.
  - While creating the instance we need to attach it to a key value pair which will act as a key to access the instance while connecting through  the shell out side the AWS. For this project i used an existing key value pair which is 'prasanna-batch7'.
  - The instance should be attached to a security group for accessing it through internet. In thius project 'default' security group is used which was configured with the neccessary ports open for the application to run. We can create a new security group as well. but remeber to add inbound rules to open the neccessary ports.
  - Samaple instance configuration is as follows:
    <img width="1111" alt="Screenshot 2024-09-25 at 3 40 36 PM" src="https://github.com/user-attachments/assets/2907ef54-1926-4be3-a9bb-82c9d77fbea1">
### 2. Instance Configuration:
  After creating the instances we need to configure the instance to run the application. Use the following steps to update install server and package manager.
  ``` sudo apt-get update
      sudo apt-get install nginx
      sudo apt-get install npm
  ```
### 3. Cone the application:
  Use git clone to clone the application. Use [this link](https://github.com/prasanna-konduri/TravelMemory) to clone the application to the /var/www/html folder of the instance. 
 
