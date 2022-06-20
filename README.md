# Automate the creation of a Consul cluster using terraform, packer and, scripting on AWS

This repo contains a set of modules in the modules folder for deploying a Consul cluster on AWS using Terraform. Consul is a distributed, highly-available tool that you can use for service discovery and key/value storage. A Consul cluster typically includes a small number of server nodes.
![image](https://user-images.githubusercontent.com/46480999/174504530-4f9e9c8c-ed6a-495f-aaeb-5ef8c30ececd.png)

Prerequisites:

AWS account IAM role with necessary permissions Terraform & AWS CLI configured on machine from which the scripts are to be run
  
# Note: You can create own AMI or skip I have tested both way. But in production recommended to create own AMI for consul cluster setup.

AMI using packer,aws cli 
    To build the Consul AMI:
    
  1. git clone this repo to your computer.
  2. Install Packer.
  3. Configure your AWS credentials using one of the options supported by the AWS SDK. Usually, the easiest option is to set the AWS_ACCESS_KEY_ID and AWS_SECRET_ACCESS_KEY environment variables.
  4. Update the variables section of the consul. json Packer template to configure the AWS region, Consul version, and Dnsmasq version you wish to use.        If you want to install Consul Enterprise, skip the version variable and instead set the download_url to the full url that points to the consul            enterprise zipped package.
   
   5. Run command to build AMI:
   
        - cd /consul_cluster_clark-/examples/consul-ami;
        - packer build consul.json;
 
# Steps for consol cluster setup

1. aws cli setup configure profile with name of default or replace if you have multiple awscli profile
   e.g: ![image](https://user-images.githubusercontent.com/46480999/174508568-ead8f81f-8467-4f17-bd09-426a9718be24.png)

3. Terraform install on which laptop/server you will be using to cloning and running code.
    - git clone https://github.com/saeed0808/consul_cluster_clark-.git;
    - cd consul_cluster_clark-;
    - terraform init;
    - terraform plan;
    - terraform apply --auto-approve;
    
# consul cluster verification
1. Go to aws console 
   1. ec2 3 ec2 should be running as defind for now 3 node cluster and in ASG min, max, desired are 3
   2. ssh to any ec2 with public ip *.pem key downloaded in same folder change permission 400
      e.g chmod 400 myKey.pem; ssh -i myKey ubuntu@54.2434.62.146 -p22
   3. To verify Consul is properly installed, run consul -v on your system
      e.g: consul version
   5. service status check
      e.g: sudo systemctl start consul
   7. Check cluster members 
      e.g: consul members
      
# You can access the consul web UI using the following URL syntax.

   - http://consul-IP:8500/ui;
  
 ![consul-ui-screenshot](https://user-images.githubusercontent.com/46480999/174506801-ede1c368-e5d5-480d-9f3c-8c1f4b27d8c2.png)

 
 


