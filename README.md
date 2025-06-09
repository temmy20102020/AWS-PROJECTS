## Project Overview 
This project is meant to design a web application in a public subnet availability zone so as to make it available for users with the help of Elastic Load Balancer.
## Objectives 
a. Design a suitable network 
b. Draw the topology to meet this requirement
c. 
## STEP 1
Design a suitable network

## STEP 2
Draw the topology to meet this requirement


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/woa1ovvwq81mwowqm992.png)





## STEP 3
Create Management VPC 

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/fr4v67mv3rvo3qs6chvi.png)


## STEP 4
Create public subnets in two availability zones, eu-west-1a and eu-west-1b, respectively.

### eu-west-1a
![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/i8l2kedsyza2rst02klc.png)

### eu-west-1b

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/6r3n1qe314z6ok07hvlm.png)

## STEP 5
Create a route table for both subnets.

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/w9gsjx1qodhqueat0j6l.png)


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/axfs4bmxkcomnpkqoeff.png)




## STEP 6
Create an AMI for an EC2 instance with a web application.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/h4jqxwl2evb115i52z3b.png)



## STEP 7
Create a target group for the application load balancer.

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/yjq90c1e25xqihw95opd.png)

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/l7ulwwtq3aua3vw2qvjq.png)



## STEP 8
Create an application load balancer.

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/s9io3imdwtfwzel9qazf.png)


## STEP 9
Create a launch template 

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/qza1xi6ktpda37h00dt5.png)


## STEP 10
Create auto-scaling group

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/obha3q1c7i9o8nww0411.png)


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/cmwlxuhmy40pegzffxm0.png)

###
Attach to load balancer 

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/i25b38y0i3migedphx6z.png)


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/jj2tqf4ba0dhml60smud.png)


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/mo5lg7576jp1hxtea6cs.png)





## STEP 11


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/9pudypqw3z7fx9x4alnd.png)


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/037oeldjsxe6f6mdepzu.png)






## STEP 12

#### elb-url (WEB-APP-LB-909414547.eu-west-1.elb.amazonaws.com)

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/rmp0jtjwuf1muich3jt9.png)


## STEP 13
## STEP 14
