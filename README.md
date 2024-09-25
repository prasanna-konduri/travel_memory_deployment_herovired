# Travel Memory Deployment
## Introduction:
  Travel memory application is developed on MERN stack. this project will explain on how to deployit on AWS with load balancer using cloudflare for DNS setup.
## Deployment steps:
### 1. Create EC2 instances:
  - To deploy the application we need instance. As the ELB is used for load balancing we are creating two instances named as pk-tm-0 and pk-tm-1.
  - While creating the instance we need to attach it to a key value pair which will act as a key to access the instance while connecting through  the shell out side the AWS. For this project i used an existing key value pair which is 'prasanna-batch7'.
  - The instance should be attached to a security group for accessing it through internet. In thius project 'default' security group is used which was configured with the neccessary ports open for the application to run. We can create a new security group as well. but remeber to add inbound rules to open the neccessary ports.
  - Instance configuration is as follows:
    <img width="1111" alt="Screenshot 2024-09-25 at 3 40 36 PM" src="https://github.com/user-attachments/assets/2907ef54-1926-4be3-a9bb-82c9d77fbea1">

### 2. Create a target group:
 Create a target group tagrgetting the two EC2 instance we created. create 'pk-tm-tg' taet group and registered the 'pk-tm-0' and 'pk-tm-1' with the target group.
![image](https://github.com/user-attachments/assets/b08da549-fe3a-4278-9aa5-51b1a67634cd)

### 3. Create a load balancer:
  Create an ELB to handele the load. In this project created a application load balancer 'pk-tm-lb' with the target group 'pk-tm-tg'. the loadbalancer configuration is as follows.
  <img width="1158" alt="Screenshot 2024-09-25 at 5 15 22 PM" src="https://github.com/user-attachments/assets/7afbe24c-d37b-4678-8b11-1bb72bd40367">
  
### 4. Instance Configuration:
  After creating the instances we need to configure the instance to run the application. Use the following steps to update install server and package manager.
  ``` sudo apt-get update
      sudo apt-get install nginx
      sudo apt-get install npm
```

### 5. Cone the application:
  Use git clone to clone the application. Use [this link](https://github.com/prasanna-konduri/TravelMemory) to clone the application to the /var/www/html folder of the instance. 

### 6. Setup and run the application:
  - To set-up the application follow the steps mentioned in the project [Readme.md](https://github.com/prasanna-konduri/TravelMemory/blob/main/README.md).

### 7. Cloudflare DNS setup:
  - Login to the cloudflare account and add the website by going to the menu->webstites> add website section.
  - Change the nameservers if the domain is not purchased from cloudflare.
  - To change the name servers
    - Login to the Domain provider site go to the domain name under which nameservers are displayed.
    - Copy the name servers provided by cloudfalre and paste them in place of your domain provider's nameservers.
  - After changing the nameservers now you are all set to use the cloudflare to maintain the website.
  - Add CNAME record.
    The coloudflare set up is as follows
    <img width="1440" alt="Screenshot 2024-09-25 at 5 58 32 PM" src="https://github.com/user-attachments/assets/0e84bf38-4fc8-495e-a8be-e5991a651601">

### 8. Configure Nginx:
  - Connect to the instance and go to /etc/nginx/sites-enabled folder and edit the default file.
  - Please find the below configuration.
    <img width="1148" alt="Screenshot 2024-09-25 at 3 58 54 PM" src="https://github.com/user-attachments/assets/a8bd7c2a-eea4-4bcb-8461-675fa0b56ae1">


## Output Screenshots:
  Afetr the completion of deployemnt the out put will be as follows:
  1. Application on loadbalancer DNS
  <img width="1440" alt="Screenshot 2024-09-25 at 12 56 11 PM" src="https://github.com/user-attachments/assets/b0c3d7c4-9a26-45b8-8839-c22ea4a905a1">
  2. Application hosted on the domain http://tm.prasannakonduri.online/
  <img width="1439" alt="Screenshot 2024-09-25 at 12 55 28 PM" src="https://github.com/user-attachments/assets/157321aa-45ea-42a7-990d-56ad35d88c17">
  3. Output from the backend.
  <img width="1433" alt="Screenshot 2024-09-25 at 12 47 12 PM" src="https://github.com/user-attachments/assets/018688dd-40e8-4558-9b60-897d95810254">

  
    

 
