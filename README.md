**Our requirement is to create VPC and two private instances with auto scaling to show work of two web servers as shown in below figure**
 
There are some steps to complete this project

![requrment](https://github.com/user-attachments/assets/c8e5bc4a-3ba0-4040-a649-6aef1f65f78c)

**STEP 1:**
1.	Go to aws console and sign-in to aws account
2.	Choose the vpc through search bar

**Note:** If we choose (vpc only) option then we have to create
      components step by step manually
  	
**STEP 2:**
1.	Create one vpc
2.	Create four subnets as two public subnets and two private subnets for private subnets choose two different availability zones
3.	Create one public route table and two private route tables
4.	Update the subnet associations as (public subnets to public routes) and (private subnets to private routes)
5.	Create one internet gateway and attach to public route tables
6.	Create one NAT gateway and attach to private route tables

**Note:** If we choose (vpc and more) option and select the components as our requirements then it will create the connections 
      automatically

1.	You can see all the component connections in preview
2.	As shown in below figure
   
   ![preview 1](https://github.com/user-attachments/assets/fe59c220-7d03-4956-adfb-c34e74228799)

 
**STEP 3:**
1.	Go to EC2 service from vpc
2.	Select the launch templates
3.	Create the launch templates and give the name for launch template
4.	Choose the instance type as free tire as shown in below figure
   
    ![launch instance3](https://github.com/user-attachments/assets/73091699-d01b-4495-9848-6cb046757264)

 
5.	Select the created key pair or generate a new key pair
6.	Update the network settings by clicking on edit option
   
      •	No need to change subnet

      •	Click on create security group
  	
      •	enter the security  group name
  	
      •	enter the description it’s your choice
  	
      •	select the created vpc for the project
  	
      •	update the inbound rules
  	
      •	one is ssh and another is http port 80
  	
      •	launch the templats
  	 
      •	do this as shown in below figure
  	
       ![launch png](https://github.com/user-attachments/assets/ecdd2d2d-f72c-4a15-8d7a-23c9b8488c78)

**STEP 4:**
1.	Go to auto scalling group
2.	Create the auto scalling group
3.	Give the name for auto scalling group
4.	Select the created launch templats
5.	Choose instance type requirement

    •	Choose VCPUs minimum and maximum
  	
    •	(2 is minimum) and (3 is maximum)
  	
    •	Choose memory minimum and maximum
  	
    •	(4 is minimum) and (8 is maximum)
  	
    •	Select as shown in below figure

       ![asg1](https://github.com/user-attachments/assets/86455c8b-e275-4fdb-88a8-f64823d56e20)

 
6.	Select created vpc
7.	Select 2 private availability zones as shown in below figure

    ![asg2](https://github.com/user-attachments/assets/0d892ce0-d294-4983-bef8-5467dc7e8c15)

  
8.	No need to select load balancer leave as no load balancer
9.	Choose desired capacity and scalling option as shown in below figure

    ![asg3](https://github.com/user-attachments/assets/24a4ca11-1411-410a-99e9-491650570e12)

 
10.	Auto scalling group is created
    
**STEP 5:**
1.	Go to instance
2.	Check the instance their 2 private instances are created from auto scalling group
3.	Give the name for 2 private instances as private 1 and private 2 to avoid confusions
4.	Create one public instance named as bastion host as shown in figure

    ![instance](https://github.com/user-attachments/assets/a7ee71c0-4b41-4fc4-87d1-b185be52d07a)

 
5.	From that public instance we can connect the private through ssh client
6.	completing the terminal work for two private instances
   
**STEP 6:**
1.	Go to target groups
2.	Create the target group 
3.	Give the name for target group
4.	Select the two private instances as shown in below figure

    ![target group](https://github.com/user-attachments/assets/fb28a041-8ebd-47f3-a271-683507fdb132)

 
5.	Click on include as pending below
6.	Click on create the target group then target group is created
   
**STEP 7:**
1.	Go to load balancer
2.	Click on create load balancer
3.	Give the name for load balancer 
4.	Update network mapping
    
    •	Choose created vpc
  	
    •	Choose two availability zones as shown in figure

      ![load balancer1](https://github.com/user-attachments/assets/be8c6ecf-3779-4c05-ac35-7642eebef686)

 
5.	Update the created security group as shown in below figure

    ![load balancer2](https://github.com/user-attachments/assets/05ca85e5-7e07-41d8-ace4-72f420cca72b)

 
6.	Click on create load balancer then load balancer is created
7.	Copy the load balancer DNS name to access the two web servers

    ![load balancer](https://github.com/user-attachments/assets/b212124b-682f-45dd-bb80-9b027ba7ba86)

   
**STEP 8:**
1.	Go to Google page or new web page
2.	 Paste the copied DNS name on URL path
3.	You can see the two created web servers as shown in figure

    ![server1](https://github.com/user-attachments/assets/331f89fc-67ed-4277-b1c6-3ef7894691aa)

  
4.	Just re-fresh the page then you see second server

    ![server2](https://github.com/user-attachments/assets/a4a78085-2011-4dda-8f93-d42c963c698d)

 
That’s it, our requirement is done.
