# terraform-aws-vpc

## overview

This Terraform module creates an AWS VPC with a given CIDR
block. It also creates multiple subnets (public and private), 
and for public subnets, it sets up an Internet Gateway (IGW)
and appropriate route tables.

## features

- creates a VPC with specified CIDR block
- creates public and private subnets 
- creates an Internet Gateway (IGW) for public subnets 
- set up route table for public subnets 

## usage 
```
module "vpc" {
  source = "./module/vpc"

  vpc_config = {
    cidr_block = "10.0.0.0/16"
    name       = "your-vpc-name"
  }
  subnet_config = {
    public_subnet = {
      cidr_block = "10.0.0.0/24"
      az         = "eu-north-1a"
      #to set the subnet as a public, default as a private 
      public     = true
    }
    private_subnet = {
      cidr_block = "10.0.1.0/24"
      az         = "eu-north-1b"
    }
  }
}


```

