# AWS VPC Project

## Steps Followed

### 1. Create VPC
- Name: my-vpc
- IPv4 CIDR: 10.0.0.0/16

### 2. Create Public Subnets
- public-subnet-a: 10.0.1.0/24, AZ: us-east-1a
- public-subnet-b: 10.0.2.0/24, AZ: us-east-1b
- Auto-assign public IP: ON

### 3. Create Private Subnets
- private-subnet-a: 10.0.11.0/24, AZ: us-east-1a
- private-subnet-b: 10.0.12.0/24, AZ: us-east-1b
- Auto-assign public IP: OFF

### 4. Internet Gateway
- Name: my internet gateway
- Attach to VPC: my-vpc

### 5. Public Route Table
- Name: public-rt
- Routes: 0.0.0.0/0 → IGW
- Subnet associations: public-subnet-1, public-subnet-2

### 6. NAT Gateway
- Subnet: public-subnet-1
- Elastic IP: Allocate new
- Name: my nat gateway

### 7. Private Route Table
- Name: private-rt
- Routes: 0.0.0.0/0 → NAT Gateway
- Subnet associations: private-subnet-1, private-subnet-2

## Screenshots
- VPC Details → Screenshots/vpc.png
- Subnets → Screenshots/subnets.png
- Public Route Table → Screenshots/public-rt.png
- Private Route Table → Screenshots/private-rt.png
- NAT Gateway → Screenshots/nat-gw.png
- Internet Gateway → Screenshots/igw.png

## Verification
- Public subnet EC2 → Can access internet directly
- Private subnet EC2 → No public IP, but outbound internet via NAT