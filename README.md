# Udacity_Project_2


The project is to Deploy a simple HTML/CSS application using auto scailing group launched in two private subnet in two difrrent AZs and a Public LoadBalancer to forward traffic to these severs
# Projetc Overview And Architecture
<!-- ![GCP horizontal framework](https://user-images.githubusercontent.com/73159522/202285588-7aefb042-b6ae-4661-8ef0-6b25666c7880.jpeg) -->

## 🛠 AWS Used Services :
| Service | Purpose |
| ------ | ------ |
| [ AWSCLI ](https://docs.aws.amazon.com/cli/index.html) | Is a unified tool that provides a consistent interface for interacting with all parts of Amazon Web Services. |
| [ VPC ](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html) | Define and launch AWS resources in a logically isolated virtual network. |
| [ CoudFormation ](https://docs.aws.amazon.com/cloudformation/index.html) | AWS CloudFormation lets you model, provision, and manage AWS and third-party resources by treating infrastructure as code. |
| [ EC2 ](https://docs.aws.amazon.com/ec2/index.html) | Amazon Elastic Compute Cloud (Amazon EC2) offers the broadest and deepest compute platform.|
| [ ELB ](https://docs.aws.amazon.com/elasticloadbalancing/index.html) | Elastic Load Balancer used to distribute network traffic to improve application scalability. |
| [ ASG ](https://docs.aws.amazon.com/autoscaling/index.html) | An Auto Scaling group contains a collection of EC2 instances that are treated as a logical grouping for the purposes of automatic scaling and management. |

## Configure Infrastructure Using CloudFormation :

ClodFormation is used to provide a stable and managed Infrastructure to the project
- ###  Network Contains The Following Resources :
  - VPC that project will be assigned to
  - Two public and private subnets
  - NAT Gateway and InternetGateWay and Router
  - Firewall to allow SSH Connection for BastionHost
  - Firewall to allow SSH and HTTP Connection for servers

## First Step: Create Infrastructure :
### 1. Clone The Repo:
```
git clone https://github.com/abdelrahman1421/Udacity_Project_2.git

```

### 2. Change Directory :
```
cd Udacity_Project_2/

```
### 3. Apply Infrastructure :
```
aws cloudformation create-stack --stack-name Final --template-body file://project.yml  --parameters file://project.json--region=us-east-1

```
![Screenshot from 2022-12-21 16-05-22](https://user-images.githubusercontent.com/73159522/208930657-18705ca9-e5ce-4a9f-a873-ca926bb6ae06.png)

![Screenshot from 2022-12-21 16-05-41](https://user-images.githubusercontent.com/73159522/208930671-b1afff58-f21a-408d-8796-7a288979e637.png)

![Screenshot from 2022-12-21 16-05-33](https://user-images.githubusercontent.com/73159522/208930663-67600022-a557-4710-8fe0-0b225e791481.png)
## 4.Hit LoadBalacerUrl :
> Now after the Infrastructure is built navigate to `Outputs` from the Stack console then click the `LoadBalacerUrl` to access the application
```
http://Final-WebAp-1TJ24RYV6BFDD-1519749287.us-east-1.elb.amazonaws.com

```

![Screenshot from 2022-12-21 16-05-46](https://user-images.githubusercontent.com/73159522/208931887-70b34dfc-ca1a-445f-8de5-833837e98e5e.png)

## Final Result
![Screenshot from 2022-12-21 16-06-56](https://user-images.githubusercontent.com/73159522/208932014-1b122a0e-04fc-4497-8350-d7109b0363d0.png)

## Clean Up Project
```
aws cloudformation delete-stack --stack-name Final --template-body file://project.yml  --parameters file://project.json--region=us-east-1
```
