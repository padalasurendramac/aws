# VPC SETUP

### Creating vpc 

  select vpc service from aws then clck on create vpc
  ![image](https://user-images.githubusercontent.com/53860717/145720061-4cf016ae-4384-4961-9ad3-e1db4d622eb3.png)


### creating Internet gateway

  Select internet gateway from aws then click on create create internet gateway
  ![image](https://user-images.githubusercontent.com/53860717/145720153-04d10b0c-dce8-46a5-91db-359571718333.png)
  
  Then select the internet gateway which is created after that click on action and seclet attach vpc 
  ![image](https://user-images.githubusercontent.com/53860717/145720417-74936d1f-e52c-493a-8ddd-d37a0b48715f.png)

  next that choose the vpc which we created above
  ![image](https://user-images.githubusercontent.com/53860717/145720458-1a4b04e8-471d-479d-af57-6c31a048750b.png)

### creating subnets ( by default elb minimum requires two subnets (availability zone us-west-2a, us-west-2b, us-west-2c, us-west-2d  ) 

  creating subnet click on subnet then chosse the vpc which we create above after give the subnet name and availability zone ( us-west-2a, us-west-2b, us-west-2c, us-west-2d) and give respective subnet ( like 172.31.1.0/24 ) then click on create subnet

### public subnet
![image](https://user-images.githubusercontent.com/53860717/145720740-7b382870-943b-46db-ba43-a7c03b24694e.png)

### subnet

                    vpc             subnet name         availability zone     CIDR SUBNET
                    
                    ABOVE VPC        work_public_2a       us-west-2a            172.31.1.0/24
                    ABOVE VPC        work_public_2b       us-west-2b            172.31.2.0/24
                    ABOVE VPC        work_private_2a      us-west-2a            172.31.3.0/24
                    ABOVE VPC        work_private_2b      us-west-2b            172.31.4.0/24

###  private subnet
![image](https://user-images.githubusercontent.com/53860717/145720958-92b00fa4-6c8d-42ca-801a-16abd18ab721.png)


### by default one route table would be created when we provision the vpc
    like below:_
    ![image](https://user-images.githubusercontent.com/53860717/145721202-641c3434-80ce-42ba-9b7e-bb4b9ab6ce45.png)

    giving the tag to default Route table to public
    ![image](https://user-images.githubusercontent.com/53860717/145721230-382101aa-76c9-440e-bec9-f7e641cf7886.png)


### Creating private route table
     give route name as private and choose the vpc which we created and click on create route table
     ![image](https://user-images.githubusercontent.com/53860717/145721370-ca72ff6b-5a7d-469d-9db9-6ef8158cb598.png)

### adding public subnet to public route rable like below
![image](https://user-images.githubusercontent.com/53860717/145721548-c7d019e9-702c-428c-a18d-cc02341c7879.png)
     
![image](https://user-images.githubusercontent.com/53860717/145721562-9a5bdd64-3fb9-4ac2-bd05-7ee0f6799cb7.png)
### adding private subnet to private route table like below:-
![image](https://user-images.githubusercontent.com/53860717/145721714-2dc70ad0-39cf-4d3b-8bca-ef946ddd6ee3.png)

![image](https://user-images.githubusercontent.com/53860717/145721728-7e73ad53-4222-48fa-b515-9b3e338a4155.png)

### adding the Internet gateway to the public route table to explore the subnet to access from internet
     
![image](https://user-images.githubusercontent.com/53860717/145721883-0ff4a733-b7c3-43f3-86b3-682e0d7d1a88.png)
![image](https://user-images.githubusercontent.com/53860717/145721897-7f38754e-df5c-4fb0-89a7-e5e6b63ab4d3.png)


### Creating NAT for private Route Table to provide internet to them 

     Give nat name, choose the public subnet with in the vpc which we created above then click on allocate elastic ip 
![image](https://user-images.githubusercontent.com/53860717/145722065-e56f6460-61ba-47af-a778-104c3a908d15.png)


### adding nat to private route table like below.
![image](https://user-images.githubusercontent.com/53860717/145722186-9def6c9d-f99b-4ac9-9cb8-cec1422a1eb0.png)

![image](https://user-images.githubusercontent.com/53860717/145722204-be0a8585-ff4e-4a20-a6a8-2cee194b70af.png)


                    
