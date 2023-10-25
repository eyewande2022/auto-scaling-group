AUTO-SCALING GROUP CONFIGURATIONS WITH LOAD BALANCER AND TARGET GROUP
The autoscaling group are the collection of Amazon EC2 instances that enables scaling to enable high availability and performance of our applications Below are the steps to creating an auto-scaling group. Step 1: Navigate to the Amazon EC2 Auto Scaling and click the “Create Auto Scaling group” button and input the ASG details and create a launch template.

![image](https://github.com/eyewande2022/auto-scaling-group/assets/116227096/e26a37f9-4705-43fe-acfa-9118a8e72ce8)

![image](https://github.com/eyewande2022/auto-scaling-group/assets/116227096/54176c6e-953e-451e-b2c1-ba8762fb842d)


Fill all relevant details and check the “Auto Scaling guidance”.


![image](https://github.com/eyewande2022/auto-scaling-group/assets/116227096/3dc02bd7-2191-4b78-b377-0f801c3d973e)


Choose Instance type


![image](https://github.com/eyewande2022/auto-scaling-group/assets/116227096/ebf88bc9-e683-4348-bbf0-4128193f7952)

We are using the configuration of the recent ly launched instance as shown below

![image](https://github.com/eyewande2022/auto-scaling-group/assets/116227096/a99f9526-4ca8-46c3-92ec-0b16799f157e)


Select keypair and don’t include subnet with the launch template

![image](https://github.com/eyewande2022/auto-scaling-group/assets/116227096/65031717-420d-430a-a166-c47a0af0df85)


Select the security group and click the “create the launch template” button

![image](https://github.com/eyewande2022/auto-scaling-group/assets/116227096/214b947b-70b5-4ccb-95ce-d070b3637fe9)


![image](https://github.com/eyewande2022/auto-scaling-group/assets/116227096/207e014d-b969-4286-b7fa-0994d1a0b4b0)

Launch template created successfully

Navigate back to the ASG page to refresh and find the newly created launch template and click “Next” button

![image](https://github.com/eyewande2022/auto-scaling-group/assets/116227096/e14c1935-1909-47ff-ae80-1f4014f99773)


Navigate to the network section

![image](https://github.com/eyewande2022/auto-scaling-group/assets/116227096/62f5bfae-dbe3-420b-9a65-a5b451b6ba30)


Select the default vpc and Select the 3 availability zones we are using and their public subnets as shown below
![image](https://github.com/eyewande2022/auto-scaling-group/assets/116227096/1529baaa-80b4-470a-abe1-4719769d7455)


Click next and navigate to the load-balancing section

![image](https://github.com/eyewande2022/auto-scaling-group/assets/116227096/12548099-d162-44c3-aaf2-b26af08408ab)


Attach the new load balancer and select the application load balancer because we are using our HTTP and HTTPS Give the load balancer a name and make sure it is internet-facing because we want to ensure our clients are able to access it.

![image](https://github.com/eyewande2022/auto-scaling-group/assets/116227096/d3fe4520-f8df-4715-af64-01103aa3b75a)


Create a target group so that our load balancer points to it

![image](https://github.com/eyewande2022/auto-scaling-group/assets/116227096/3e16927a-0cf4-4597-bb09-40ca7b94c44f)


Once created select the new target group


![image](https://github.com/eyewande2022/auto-scaling-group/assets/116227096/2e9a5fc3-b3de-42cd-bbc7-34fc55843edd)

Take note of the health check grace period which was set to default 300 seconds .This is the time it takes for the instance to initialize .Click next to proceed .

![image](https://github.com/eyewande2022/auto-scaling-group/assets/116227096/22bbf9e5-c03d-4ede-aecf-31129d27676f)


We would need to configure the ASG poilicies . In this case our desired and minimum capacity would be set at 3 and maximum capacity would be set at 7

![image](https://github.com/eyewande2022/auto-scaling-group/assets/116227096/54973f26-82f4-41a3-b516-475c22391fe1)


Skip SNS notification and tags options

![image](https://github.com/eyewande2022/auto-scaling-group/assets/116227096/eb803fab-67d7-476d-abb6-51d40faccafb)

![image](https://github.com/eyewande2022/auto-scaling-group/assets/116227096/5f3d1003-7145-4ece-8974-3161736341a7)



Click to create “Auto scaling group” button. Observe it is updating and creating our new instance and can be seen when you check the EC2 instance page as shown below

![image](https://github.com/eyewande2022/auto-scaling-group/assets/116227096/59395a31-e11a-4216-9342-3c4dbaf67c31)


![image](https://github.com/eyewande2022/auto-scaling-group/assets/116227096/6ad209ab-6f68-418f-a4bd-02b0455a56d6)

![image](https://github.com/eyewande2022/auto-scaling-group/assets/116227096/4fa9a113-ab01-45c5-8a01-c965c4330863)

![image](https://github.com/eyewande2022/auto-scaling-group/assets/116227096/4eeae7f7-8aad-44f7-9f5f-a24846ecb428)




3 instances running and as we can see theLoad Balancer is active

![image](https://github.com/eyewande2022/auto-scaling-group/assets/116227096/e58f22ba-89d3-48fb-b740-b3ebbdec59ae)


Our target group is created but appears none is healthy and the 3 are unhealthy.

![image](https://github.com/eyewande2022/auto-scaling-group/assets/116227096/5fa579c8-2454-4ac2-bdb5-831a64c3d97d)


This is because we haven’t installed or updated the application which would be done on 2 of the servers now

We go into our application to install httpd and create an application on our server as shown below.

![image](https://github.com/eyewande2022/auto-scaling-group/assets/116227096/d902c661-0624-48d8-a5bc-e1bd87c71642)



![image](https://github.com/eyewande2022/auto-scaling-group/assets/116227096/e7a73d0e-c5ac-4569-89b4-bc2fd0f47cf1)



![image](https://github.com/eyewande2022/auto-scaling-group/assets/116227096/7d2fe560-4471-4425-a59d-01b182d7941f)

Launch on the browser to see the first server

![image](https://github.com/eyewande2022/auto-scaling-group/assets/116227096/7c7e192c-00b6-47a1-8806-0a4a9bb58d5b)


![image](https://github.com/eyewande2022/auto-scaling-group/assets/116227096/ea4c6222-5cbe-46c8-901b-1748c2771ec5)

Carrying out the same tasks for the second project server we get this below

Navigate back to the target group and we can confirm the healthy checks below

![image](https://github.com/eyewande2022/auto-scaling-group/assets/116227096/7f9706a0-f607-4f7f-bb2d-8a93b7693325)


Check the load balancer if working as expected

![image](https://github.com/eyewande2022/auto-scaling-group/assets/116227096/2fe4d720-a050-48c6-a47a-57c2fa5ab614)


Having confirmed this . Check the security group of the Load balancer to confirm if it is working with the one we assigned to the ASG and change it to the correct one

![image](https://github.com/eyewande2022/auto-scaling-group/assets/116227096/e28f3381-cbb1-45fe-b0e4-2770639210d9)


![image](https://github.com/eyewande2022/auto-scaling-group/assets/116227096/d9c7d778-0eff-4092-93f0-d9146cb787a1)


Check the load balancer if its working properly

![image](https://github.com/eyewande2022/auto-scaling-group/assets/116227096/e605d30b-3b01-45ea-8383-316d9eff1915)


![image](https://github.com/eyewande2022/auto-scaling-group/assets/116227096/a7457112-6775-42c6-a6ec-45bbab2b5818)


Our LB is working perfectly hence we have concluded to set up our ASG successfully with the target group,load balancer as well.

Please note : Remember to terminate all infrastructure as they would accrue costs if you are conducting a demo.

Thanks
