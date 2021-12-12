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



                    
