# AWS Environment

This repository contains the cloudformation scripts and ansible playbooks neccessary to deploy a 
* VPC
* NACL
* Security Group
* Bastion Instance

## Setup
* brew install python
* brew install ansible
* git clone https://github.com/thadgholston/aws-environment

## How to deploy
Copy the template inventory file and replace the values in group_vars/all with the applicable values for your environment.

Run `ansible-playbook -i inventories/{{ your inventory name }} environment.yaml`

You should be able to ssh into the bastion instance with 

`ssh -i ~/.ssh/admin_keypair {{ bastion host eip }}`

You can find the bastion host eip in the EC2 Console. 

To teardown the environment run ``ansible-playbook -i inventories/{{ your inventory name }} tear_down.yaml`. This will leave up the elastic ips, so that you can continue to refer to those in your ~/.ssh/config file


## Future Improvements

1. Get CI/CD Pipeline to ECS Fargate Cluster working with RDS in private subnet
2. Update the templates to use nested stacks
3. Rewrite in Terraform