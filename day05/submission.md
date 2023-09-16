# TerraWeek Day 5


## Task 1: 
- What are **modules** in Terraform and why do we need modules in Terraform?

In Terraform, modules are a way to encapsulate and organize your infrastructure code into reusable and shareable components. They allow you to break down your Terraform configurations into smaller, more manageable pieces, making it easier to maintain and scale your infrastructure as code (IaC) projects.

- What are the benefits of using modules in Terraform?

Modules offer several benefits:

Reusability: You can create modules once and reuse them across different Terraform configurations.
Abstraction: Modules abstract the complexity of resources, making your main configuration files cleaner and more focused on high-level architecture.
Collaboration: Teams can collaborate more effectively by sharing modules that encapsulate best practices and standards.
Testing: Modules can be tested in isolation, making it easier to ensure their correctness before using them in various configurations.

## Task 2: 
- Create/Define a module in Terraform to encapsulate reusable infrastructure configuration in a modular and scalable manner. For e.g. $\textcolor{yellow}{\textsf{EC2 instance in AWS}}$, $\textcolor{lightblue}{\textsf{Resource Group in Azure}}$, $\textcolor{red}{\textsf{Cloud Storage bucket in GCP}}$.

Create main.tf

      #dev infra
      
      module "dev-demo-app" {
              source = "./modules/demo-app"
              instance_type = "t2.micro"
              env_name = "dev"
              ami_id = "ami-053b0d53c279acc90"
              instance_name = "demo-instance"
              bucket_name = "my-example-terra-project-bucket"
              table_name = "demo-table"
      
      }
      
      
      
      #qa infra
      
      module "qa-demo-app" {
              source = "./modules/demo-app"
              instance_type = "t2.small"
              env_name = "qa"
              ami_id = "ami-04cb4ca688797756f"
              instance_name = "demo-instance"
              bucket_name = "my-example-terra-project-bucket"
              table_name = "demo-table"
      
      }
      
      
      
      #prod infra
      
      module "prod-demo-app" {
              source = "./modules/demo-app"
              instance_type = "t2.medium"
              env_name = "prod"
              ami_id = "ami-026ebd4cfe2c043b2"
              instance_name = "demo-instance"
              bucket_name = "my-example-terra-project-bucket"
              table_name = "demo-table"
      
      }

<img width="373" alt="image" src="https://github.com/ManishNegi963/TerraWeek/assets/124788172/92fa0399-0c83-4bcc-b737-e3fb088e3585">




## Task 3: 
- Dig into **modular composition** and **module versioning**.

  In Terraform, modular composition refers to the practice of organizing your infrastructure code into reusable and composable modules. This approach allows you to break down your Terraform configurations into smaller, self-contained components that can be combined to build complex infrastructure deployments. Modular composition in Terraform offers several benefits:

Code Reusability: With modular composition, you can create modules for common infrastructure patterns, such as virtual machines, databases, or load balancers, and reuse these modules across different Terraform configurations. This reduces code duplication and promotes consistency.

 * Module versioning:

   Module versioning is an important practice in Terraform that allows you to manage and control the versions of modules used in your infrastructure code. By specifying module versions, you can ensure that your infrastructure remains consistent and stable, even as you make updates and changes to your codebase. Here's an overview of module versioning in Terraform:

Key Concepts:

Module Versioning: Terraform modules can have different versions, just like software packages. Each version represents a specific state of the module's code and configuration. Version numbers are typically in the form of x.y.z, where x represents the major version, y represents the minor version, and z represents the patch version. 

## Task 4: 
- What are the ways to **lock Terraform module versions**? Explain with code snippets.

- Using the LockID in dynamodb table to lock the version in remote state
  <img width="227" alt="image" src="https://github.com/ManishNegi963/TerraWeek/assets/124788172/5a9aabd0-3172-4515-af48-41755cbbc8d7">

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
  

<img width="318" alt="image" src="https://github.com/ManishNegi963/TerraWeek/assets/124788172/0f21c57c-4ad3-46a4-b439-d45580aa2cca">


<br>
Attach code snippets and steps wherever necessary and post your learnings on LinkedIn with #TerraWeek tag.

Feel Free to reach out to any of the TWS Community Builders / Leaders.

Happy Learning 😊

