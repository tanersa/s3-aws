****_Steps to create S3 Bucket by provisioning the infrastructure with CFT_****

  - As we refer the AWS Documentation, we can see that we need to begin writing our json file with template format version and description.

          "AWSTemplateFormatVersion" : "2010-09-09",
          "Description": "This CFT provisions AWS S3",
          
   - Next would be defining our parameters starting with our key, so we can have privilege to access our EC2 instance using ssh agent.

           "Parameters": {
                "KeyName": {
                    "Description": "This key will be used to SSH to our EC2 instances",
                    "Type": "AWS::EC2::KeyPair::KeyName"
                },
                
   -  Other parameters we need to add are Virtual Private Cloud (VPC), subnet, and instance type info with stating types and default values. Based on our data that 
      we are aiming to store in S3 Bucket we may increase the size of our instance type.
      
      
             "myVPC": {
                  "Description": "Use DevOps VPC",
                  "Type": "String",
                  "Default": "vpc-ea4d2f97"
              },
              "mySubnet": {
                  "Description": "Use DevOps Subnet",
                  "Type": "String",
                  "Default": "subnet-d10d68e0"
              },
              "InstanceType": {
                  "Description": "EC2 instance types",
                  "Type": "String",
                  "Default": "t2.micro",
                  "AllowedValues": ["t2.micro", "t2.small"]
              }

    