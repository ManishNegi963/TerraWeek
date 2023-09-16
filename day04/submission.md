# TerraWeek Day 4 🌱

## Task 1: Importance of Terraform State

📚 **Research**: Dive into the importance of Terraform state in managing infrastructure. Discover how Terraform state helps track the current state of resources and ensures smooth infrastructure provisioning and management.

Terraform is an infrastructure as code (IaC) tool that allows you to define and provision infrastructure resources in a declarative manner. The Terraform state is a crucial aspect of how Terraform manages and tracks the resources it creates and manages.

Here are some key points about Terraform state:

* State File: Terraform uses a state file to keep track of the resources it manages. This file is typically named terraform.tfstate, and it contains information about the current state of your infrastructure, including resource IDs, attributes, and metadata.

* Remote and Local State: Terraform supports both local and remote state. Local state files are stored on the machine where you run terraform apply, while remote state is stored in a shared location, often a remote storage service like Amazon S3 or HashiCorp Consul.

* Concurrency and Locking: When multiple team members work on the same Terraform configuration, locking mechanisms prevent concurrent updates to the state to avoid conflicts.

* Resource Dependency Tracking: Terraform uses the state to track dependencies between resources. When you make changes to your configuration and run terraform apply, Terraform uses the state to determine the order in which resources should be created, updated, or destroyed.

* Sensitive Data: Sensitive data, such as passwords or private keys, should not be stored in the state file. Terraform provides mechanisms for marking sensitive values so that they are not displayed in the output and can be securely managed.

* State Management: Terraform commands like terraform init, terraform apply, and terraform destroy interact with the state to plan and apply changes to your infrastructure.

* Remote State Backends: Popular remote state backends include Amazon S3, Azure Blob Storage, Google Cloud Storage, and HashiCorp Consul. These backends provide features like state locking, versioning, and access control.

* Here's an example of using a remote state backend with Amazon S3:


      terraform {
        backend "s3" {
          bucket         = "my-terraform-state"
          key            = "terraform.tfstate"
          region         = "us-east-1"
          encrypt        = true
          dynamodb_table = "terraform-lock-table"
        }
      }
In this example, Terraform is configured to store the state file in an S3 bucket named "my-terraform-state," enabling state locking with a DynamoDB table named "terraform-lock-table."

Managing the Terraform state is critical for maintaining the integrity and consistency of your infrastructure. By using a remote state backend and following best practices, you can ensure that your state is secure, accessible to your team, and protected against concurrent changes.


## Task 2: Local State and `terraform state` Command

📚 **Understand**: Explore different methods of storing the state file, such as local or remote storage. Create a simple Terraform configuration file and initialize it to generate a local state file. Get hands-on with the `terraform state` command and learn how to use it effectively to manage and manipulate resources.

Storing terraform state file locally: terraform create terraform.tfstate when we run the command terraform apply

- Create terraform.tf

<img width="431" alt="image" src="https://github.com/ManishNegi963/TerraWeek/assets/124788172/a2609cb0-b55d-4b9f-855c-30ebc623a85d">

- Mention provider and create resource s3 bucket in main.tf

<img width="316" alt="image" src="https://github.com/ManishNegi963/TerraWeek/assets/124788172/053c9081-2567-4faa-9757-9c7f8a015407">

- Use terraform init to initialize the aws plugins and then apply to create terraform.tfstate file

<img width="443" alt="image" src="https://github.com/ManishNegi963/TerraWeek/assets/124788172/f9e1c170-f06a-4a14-b662-e1b1fe515e56">

- terraform local state file has been generated which stores the state.

 <img width="501" alt="image" src="https://github.com/ManishNegi963/TerraWeek/assets/124788172/3fd00a13-0002-4bd0-8524-b545e7f41be3">

 - Using terraform state commands

 - To show a list of resources

       terraform state list

<img width="447" alt="image" src="https://github.com/ManishNegi963/TerraWeek/assets/124788172/c616a41b-a46d-4696-a89a-061a1416a25a">

- To manually download and output the state from the state file.

      terraform state pull

<img width="561" alt="image" src="https://github.com/ManishNegi963/TerraWeek/assets/124788172/0d2c24d2-87bb-45b7-aef7-9513efb977bc">

-To show attributes of a single resource from the state file.

    terraform state show aws_s3_bucket.my_bucket

<img width="637" alt="image" src="https://github.com/ManishNegi963/TerraWeek/assets/124788172/31013207-bf26-4d5f-ba59-60b3443b5354">




## Task 3: Remote State Management

📚 **Explore**: Delve into remote state management options like Terraform Cloud, AWS S3, Azure Storage Account, or HashiCorp Consul. Select one remote state management option and thoroughly research its setup and configuration process. Become familiar with the steps required to leverage remote state management in your Terraform workflow.

- Create terraform.tf

            terraform {
              required_providers {
                      aws = {
                              source = "hashicorp/aws"
                              version = "~>5.0"
      
                  }
              }
        }

  <img width="359" alt="image" src="https://github.com/ManishNegi963/TerraWeek/assets/124788172/432f70ba-7cbf-4d0c-9b61-d0ef49c1534b">

  - Create main.tf to create resource and provider.
 
            provider "aws" {
                region = "us-east-1"
        }
        
        resource "aws_instance" "my_instance" {
                instance_type = "t2.micro"
                ami = "ami-053b0d53c279acc90"
                tags = {
                        Name = "remote-test-instance"
                }
        
        
        }
        
        resource "aws_s3_bucket" "my_bucket" {
                bucket = "remote-state-buckets3"
        }
        
        resource "aws_dynamodb_table" "my_table" {
                name  = "my-remote-state-table"
                billing_mode = "PAY_PER_REQUEST"
                hash_key = "LockID"
                attribute {
                        name = "LockID"
                        type = "S"
                }
        
        }
 
    <img width="332" alt="image" src="https://github.com/ManishNegi963/TerraWeek/assets/124788172/3dcbe36c-39f2-46ba-b804-44ca7bcdf250">


- Run terraform init to install the plugin and terraform apply which will create terraform.tfstate file

      terraform init

  <img width="553" alt="image" src="https://github.com/ManishNegi963/TerraWeek/assets/124788172/0f852f1a-341d-4bae-9878-3fcc90554cda">

      terraform apply

<img width="550" alt="image" src="https://github.com/ManishNegi963/TerraWeek/assets/124788172/2305704c-0991-4d81-bccd-282f4d6e03f5">


## Task 4: Remote State Configuration

📚 **Modify**: Enhance your Terraform configuration file to store the state remotely using the chosen remote state management option. Include the necessary backend configuration block in your Terraform configuration file to enable seamless remote state storage and access.

```hcl
terraform {
  backend "<chosen_backend>" {
    # Add required configuration options for the chosen backend
  }
}
```

- Creating backend for remote state

      backend "s3" {
              bucket = "remote-state-buckets3"
              dynamodb_table = "my-remote-state-table"
              key = "terraform.tfstate"
              region = "us-east-1"
      
      
              }

  <img width="387" alt="image" src="https://github.com/ManishNegi963/TerraWeek/assets/124788172/507f1291-24b5-4484-bd88-4eb756cfeee8">

  - Run the command terraform init to initialise the remote backend.
 
        terraform init


<img width="591" alt="image" src="https://github.com/ManishNegi963/TerraWeek/assets/124788172/499056a9-47c4-4f5f-b0d0-c4422f3624bb">

- Remote state has been setup on s3.

<img width="929" alt="image" src="https://github.com/ManishNegi963/TerraWeek/assets/124788172/31eae69d-a623-4c72-bfb0-1cae25660d89">



Attach code snippets and steps wherever necessary and post your learnings on LinkedIn

Feel Free to reach out to any of the TWS Community Builders / Leaders

Watch these videos 👉 [https://youtu.be/kqJIKjkJ1Lo](https://youtu.be/kqJIKjkJ1Lo) && [https://youtu.be/VyB_vETjvT0 ](https://youtu.be/2ZwkX5Kl7vs)

Happy Learning 


