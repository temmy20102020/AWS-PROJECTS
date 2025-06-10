# Deployment of a Web Application Across Multiple Availability Zones (AZs) Within a VPC

## Project Overview 
The primary objective of this project is to design and implement a highly available and scalable web application infrastructure within Amazon Web Services (AWS). The application will be deployed across multiple Availability Zones (AZs) within a Virtual Private Cloud (VPC) to ensure redundancy, fault tolerance, and load distribution.

## Objectives 

- Designing a custom VPC with appropriate public subnets across two Availability Zones (eu-west-1a and eu-west-1b).
- Deploying a web server with Apache and a sample web page.
- Creating an Amazon Machine Image (AMI) for EC2 replication.
- Configuring an Application Load Balancer (ALB) to evenly distribute traffic.
- Setting up Auto Scaling Groups to handle variable traffic loads and improve fault tolerance.
- Ensuring the entire setup is resilient, scalable, and publicly accessible through the ALB endpoint.

## STEP 1 : Design a suitable network


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/2vw2twvnpwnhohaqwoc0.png)



## STEP 2 : Draw the topology to meet this requirement



![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/woa1ovvwq81mwowqm992.png)





## STEP 3 : Create Management VPC 


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/fr4v67mv3rvo3qs6chvi.png)


## STEP 4 :Create public subnets in two availability zones, eu-west-1a and eu-west-1b, respectively.


### eu-west-1a
![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/i8l2kedsyza2rst02klc.png)

### eu-west-1b

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/6r3n1qe314z6ok07hvlm.png)

## STEP 5: Create a Route Table for Each Subnet.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/w9gsjx1qodhqueat0j6l.png)


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/axfs4bmxkcomnpkqoeff.png)


## STEP 6: Create an EC2 Instance and Install the Web Application on It

###  Create an EC2 instance

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/5sx5f4c58gg1qispsbeo.png)



###  Install Apache
-----------------------
sudo apt update
sudo apt install apache2 -y

###  Empty apache file using tee with /dev/null
sudo tee /var/www/html/index.html < /dev/null

###  Create the HTML file
sudo nano /var/www/html/index.html
- Paste your HTML code into the file.
- Save and exit (CTRL+O, ENTER, then CTRL+X)

### Restart the web server

sudo systemctl restart apache2




## STEP 7 : Create an AMI from the EC2 Instance Running the Web Application.



![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/h4jqxwl2evb115i52z3b.png)



## STEP 8: Create a Target Group for the Application Load Balancer.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/yjq90c1e25xqihw95opd.png)

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/l7ulwwtq3aua3vw2qvjq.png)



## STEP 9: Create an Application Load Balancer  


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/s9io3imdwtfwzel9qazf.png)


## STEP 10 : Create a launch template 


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/qza1xi6ktpda37h00dt5.png)


## STEP 11 : Create an Auto Scaling Group


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/obha3q1c7i9o8nww0411.png)


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/cmwlxuhmy40pegzffxm0.png)

###
Attach to load balancer 

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/i25b38y0i3migedphx6z.png)


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/jj2tqf4ba0dhml60smud.png)


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/mo5lg7576jp1hxtea6cs.png)





## STEP 12 : Each of the two instances is running in a different Availability Zone.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/9pudypqw3z7fx9x4alnd.png)


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/037oeldjsxe6f6mdepzu.png)






## STEP 13 : Copy the DNS Name of the Elastic Load Balancer and Access It via a Web Browser.

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/2adu6x94vqeqeu3q02yy.png)


#### elb-url (WEB-APP-LB-909414547.eu-west-1.elb.amazonaws.com)

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/rmp0jtjwuf1muich3jt9.png)


## Conclusion

This project successfully demonstrated the end-to-end deployment of a web application across multiple Availability Zones within a custom Virtual Private Cloud (VPC) on AWS. By designing a robust network architecture and leveraging key AWS services such as EC2, AMI, Application Load Balancer (ALB), and Auto Scaling Groups, the solution achieved high availability, scalability, and fault tolerance.

The use of public subnets in multiple Availability Zones ensured that the web application remained accessible even in the event of an AZ failure. The load balancer provided efficient traffic distribution, while the launch template and auto-scaling configuration enabled the infrastructure to adapt dynamically to varying workloads.

This deployment aligns with cloud architecture best practices and lays a strong foundation for building resilient, performant, and scalable web applications in the cloud. Future improvements could include implementing HTTPS with SSL/TLS, using a database in private subnets, and integrating monitoring and logging with CloudWatch for better visibility and maintenance.

