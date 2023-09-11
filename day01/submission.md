# TerraWeek Day 1

## Day 1: Introduction to Terraform and Terraform Basics

# What is Terraform and how can it help you manage infrastructure as code?

Terraform is an open-source infrastructure as code (IaC) tool developed by HashiCorp. It is designed to help you manage and provision infrastructure resources in a predictable, automated, and version-controlled way. Here's how Terraform works and how it can help you manage infrastructure as code:

Infrastructure as Code (IaC): Terraform allows you to define your entire infrastructure stack using code. This code is written in a domain-specific language called HashiCorp Configuration Language (HCL) or in JSON format. With IaC, you can describe your infrastructure as code, just like you would with application code. This provides several benefits:

Version Control: You can store your infrastructure code in version control systems like Git, enabling collaboration, change tracking, and rollbacks.

Reusability: You can create modular configurations and reusable modules for different components of your infrastructure, making it easier to maintain and share best practices.

Documentation: The code itself serves as documentation for your infrastructure, making it easier for team members to understand and contribute.

Declarative Syntax: In Terraform, you declare the desired end-state of your infrastructure. You specify the resources you want (e.g., virtual machines, networks, databases), their configurations, and relationships. Terraform takes care of determining the actions required to reach that desired state.

Provider-Based: Terraform supports a wide range of infrastructure providers, including cloud providers like AWS, Azure, and Google Cloud, as well as on-premises solutions. Each provider has its own set of resource types and configurations, which Terraform abstracts and manages through provider plugins.

Dependency Management: Terraform automatically manages resource dependencies. It understands the relationships between resources and ensures they are created, updated, or destroyed in the correct order.

Plan and Apply: Terraform operates in two main phases. First, you run terraform plan to generate an execution plan that shows the changes Terraform will make to achieve the desired state. Then, you apply the plan using terraform apply to make the changes to your infrastructure. This helps prevent unexpected changes and allows for review before execution.

State Management: Terraform maintains a state file that records the current state of your infrastructure. This state file is crucial for Terraform to understand what resources it's managing and how they relate to each other. It's typically stored remotely in a backend, ensuring consistency among team members.

Scalability and Automation: Terraform is highly scalable and can manage infrastructure across multiple environments and cloud providers. It supports automation, allowing you to easily create and manage infrastructure for development, testing, staging, and production environments.




# Why do we need Terraform and how does it simplify infrastructure provisioning?

Terraform is a valuable tool in the field of infrastructure management for several reasons, and it simplifies infrastructure provisioning in the following ways:

Automation: Terraform automates the provisioning and management of infrastructure resources. Instead of manually setting up servers, networks, and other resources, you define your infrastructure as code using Terraform configurations. This automation eliminates human errors, reduces manual intervention, and saves time.

Repeatability: Infrastructure as code (IaC) with Terraform allows you to define your infrastructure in a repeatable manner. You can use the same Terraform configurations to create identical infrastructure environments in multiple locations or for different stages of your application development, ensuring consistency and reducing configuration drift.

Version Control: Terraform configurations are code, and you can store them in version control systems like Git. This provides versioning, auditing, and collaboration benefits. You can track changes to your infrastructure code, collaborate with team members, and easily roll back to previous configurations if needed.

Scalability: Terraform scales with your infrastructure needs. Whether you need to provision a single virtual machine or an entire complex infrastructure stack with thousands of resources, Terraform can handle it. You can define and manage infrastructure at any scale with the same codebase.

Cross-Platform and Provider Support: Terraform is provider-agnostic, which means you can use it to manage infrastructure on various cloud providers (AWS, Azure, GCP), on-premises environments, and third-party services. This flexibility simplifies the process of working with multiple providers and avoids vendor lock-in.

Dependency Resolution: Terraform understands resource dependencies and creates resources in the correct order. For example, it will ensure that a database is created before a web server that relies on it. This automatic dependency resolution simplifies configuration and avoids manual ordering issues.

Change Management: Terraform's "plan" functionality (via terraform plan) allows you to preview changes before applying them. This helps you understand what Terraform will do and provides an opportunity to review and validate changes, reducing the risk of unintended or destructive modifications to your infrastructure.

State Management: Terraform maintains a state file that tracks the actual state of your infrastructure. This state file enables Terraform to determine what changes are required to bring your infrastructure to the desired state. State management ensures that Terraform knows the current state of your resources, even when infrastructure changes occur outside of Terraform.

Modularity: Terraform supports modularization, allowing you to create reusable modules for common infrastructure patterns. These modules can be shared across projects, enhancing code reuse and maintaining best practices.

Ecosystem: Terraform has a vibrant ecosystem with a vast community, extensive documentation, and numerous third-party modules and providers available. This ecosystem simplifies the adoption of best practices and accelerates infrastructure development.




## How can you install Terraform and set up the environment for AWS, Azure, or GCP?

## First, install repository addition dependencies:

    sudo apt update
    sudo apt install  software-properties-common gnupg2 curl

  <img width="481" alt="image" src="https://github.com/ManishNegi963/TerraWeek/assets/124788172/f7083fe0-f31c-4083-9c24-3e5ee9c4ebab">

## Now import repository GPG key

    curl https://apt.releases.hashicorp.com/gpg | gpg --dearmor > hashicorp.gpg
    sudo install -o root -g root -m 644 hashicorp.gpg /etc/apt/trusted.gpg.d/

  <img width="731" alt="image" src="https://github.com/ManishNegi963/TerraWeek/assets/124788172/55a2e06f-c040-420a-9c13-2f25fcfb510e">

## With the key imported now add Hashicorp repository to your Ubuntu system:

      sudo apt-add-repository "deb [arch=$(dpkg --print-architecture)] https://apt.releases.hashicorp.com $(lsb_release -cs) main"

<img width="849" alt="image" src="https://github.com/ManishNegi963/TerraWeek/assets/124788172/5c008658-6ba8-4036-8744-465379576798">

## Now install terraform on your Ubuntu Linux system:

    sudo apt install terraform

  <img width="651" alt="image" src="https://github.com/ManishNegi963/TerraWeek/assets/124788172/e50abc10-7731-42c3-89ab-edc39705710d">

## Check the version of terraform installed on your system

    terraform --version

  <img width="385" alt="image" src="https://github.com/ManishNegi963/TerraWeek/assets/124788172/08a9d59c-083c-4c42-a289-1b359a2b56d8">

  ## Setting up environment for AWS

- Create a file terraform.tf

      vim terraform.tf


- Explain the important terminologies of Terraform with the example at least (5 crucial terminologies).

Attach code snippets and steps wherever necessary and post your learnings on LinkedIn

Feel Free to reach out to any of the TWS Community Builders / Leaders

Watch this [Reference Video](https://www.youtube.com/live/965CaSveIEI?feature=share)

Happy Learning 

