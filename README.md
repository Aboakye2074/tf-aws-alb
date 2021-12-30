# Create AWS ALB Using Terraform

This repo will use Terraform to create an ALB in AWS. It will install an Apache webserver.

## Resources

The following resources will be set up by each of the modules

## VPC
- 4 public subnets (configurable)
- Internet Gateway (IGW)
- A route table for the subnets to the IGW 


## AutoScaling Group (ASG)
- A SSH Key Pair (uses the public key as mentioned in the Prerequisites section)
- A security group that allows requests to/from the internet
- An EC2 Launch template that sets up an Apache webserver, and creates a default page with instance and EC2 metadata
- An Application Load Balancer (ALB) fronting the ASG

## IAM
- A policy that authorises usage of AWS API to consume EC2 metadata
- A resource policy that authorises the EC2 instances to assume the above role

## Prerequisites

- An AWS CLI profile as described [here](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-profiles.html). This project assumes that the profile is called "acg". If you want to use a different profile or the default AWS profile, then change the corresponding entry in the `variables.tf` file in the root directory
- An SSH key, stored in `~/.ssh/id_rsa.pub` or `%USERPROFILE%/.ssh/id_rsa.pub`