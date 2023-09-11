# TerraWeek Day 2

## Task 1: Familiarize yourself with HCL syntax used in Terraform
- Learn about HCL blocks, parameters, and arguments

  In the below image block is resource, parameter is "docker_image"(resources type) "nginx-img-rsc" (resource name), argument is lines written in {ame = "nginx:latest" keep_locally = false}

<img width="344" alt="image" src="https://github.com/ManishNegi963/TerraWeek/assets/124788172/5c12e524-981d-4888-ab1f-8cc6f9cd77d5">



  
- Explore the different types of resources and data sources available in Terraform

  resource docker container

  <img width="352" alt="image" src="https://github.com/ManishNegi963/TerraWeek/assets/124788172/d6086d6e-e719-4c15-a20f-7cdfc2c5fb41">

  resource local file

  <img width="492" alt="image" src="https://github.com/ManishNegi963/TerraWeek/assets/124788172/9b2534c3-9f56-4198-bf28-f7f93359eb8d">


## Task 2: Understand variables, data types, and expressions in HCL
- Create a variables.tf file and define a variable

      vim variable.tf

<img width="572" alt="image" src="https://github.com/ManishNegi963/TerraWeek/assets/124788172/11dedf1e-a3e9-4d85-b100-4bd4232f62e5">




- Use the variable in a main.tf file to create a "local_file" resource

      vim main.tf

<img width="361" alt="image" src="https://github.com/ManishNegi963/TerraWeek/assets/124788172/e246417f-5c97-4c54-a389-952673665f54">




## Task 3: Practice writing Terraform configurations using HCL syntax
- Add required_providers to your configuration, such as Docker or AWS

      vim terraform.tf

  <img width="319" alt="image" src="https://github.com/ManishNegi963/TerraWeek/assets/124788172/70df4b13-fd8d-42c8-bae6-0639cdaa3241">




- Test your configuration using the Terraform CLI and make any necessary adjustments


<img width="170" alt="image" src="https://github.com/ManishNegi963/TerraWeek/assets/124788172/f87add12-bb28-4ab1-be7d-18c4c0f2f8f1">

  --

<img width="319" alt="image" src="https://github.com/ManishNegi963/TerraWeek/assets/124788172/f07a72f7-e526-48a3-abd7-f67d535293cc">


  --

<img width="369" alt="image" src="https://github.com/ManishNegi963/TerraWeek/assets/124788172/ee178241-2536-4c82-9328-cc434a9cb279">



Attach code snippets and steps wherever necessary and post your learnings on LinkedIn
Feel Free to reach out to any of the TWS Community Builders / Leaders
Watch this 👉 https://youtu.be/kqJIKjkJ1Lo

# Happy Learning🎉🚀
