# WordPress Assignment

Deploys WordPress in AWS using Terraform and Chef

### Terraform script deploys following resources in us-west-2 region
-  VPC
-  Public Subnet
-  Internet Gateway
-  Security Group allowing ports 22, 80 and 443. Presently open to 0.0.0.0/0
-  Route table and route table association
-  RHEL7.6 EC2 instance with a user data script for cloud-init
#### Variables such as VPC/Subnet CIDR's, AMI, region, instance type, etc are specified in vars.tf file
#### Successful terraform execution displays public IP of the instance that is hosting WordPress
#### During EC2 deployment, userdata script performs the following steps
-  Chefdk installed 
-  Chef recipes needed for installation of apache, php, mariadb and wordpress are cloned from my GitHub repo
-  Chef-solo executes all recipes specified in the run list
-  Recipes also create wordpress db, set root password for mariadb and configure wordpress config file for DB connection.
