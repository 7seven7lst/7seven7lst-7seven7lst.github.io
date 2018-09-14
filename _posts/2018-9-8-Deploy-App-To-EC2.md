---
layout: post
title: Deploy NodeJS App to AWS EC2!
---

Deploy NodeJS App to AWS EC2.

* Create EC2 Instance
  1. find  EC2 ![find  EC2]({{ site.baseurl }}/images/deploy_ec2/find_EC2.png "find EC2")
  2. Filter "Free Tier Only", Select "Ubuntu" ![select EC2 type]({{ site.baseurl }}/images/deploy_ec2/select_EC2_type.png "select EC2 type")
  4. Select "t2.micro (free tier)" ![Filter Free Tier Only]({{ site.baseurl }}/images/deploy_ec2/choose_free_tier.png "Filter Free Tier Only")
  5. launch instance ![launch EC2 instance]({{ site.baseurl }}/images/deploy_ec2/launch_EC2.png "launch EC2 instance")
* Generate a Key file and download it
  1. generate and download the key ![Generate PEM key]({{ site.baseurl }}/images/deploy_ec2/generate_pem_key.png "Generate PEM key")
* SSH into the EC2 instance with your key file
  1. open terminal ![macos x terminal cd into PEM key directory]({{ site.baseurl }}/images/deploy_ec2/mac_terminal.png "macos x terminal cd into PEM key directory")
  2. cd into the directory that has the key you downloaded. for example, if you save the key in Desktop:
  ```bash
  cd ~/Desktop
  ```
  3. Find instructions on how to connect to EC2 via SSH. In terminal, type the command that change the key access mod, and SSH into EC2 ![find connection info for EC2]({{ site.baseurl }}/images/deploy_ec2/get_EC2_connection_info.png "find connection info for EC2") ![SSH into EC2]({{ site.baseurl }}/images/deploy_ec2/instruction_how_to_connect_EC2.png "SSH into EC2")
* Clone down the app into EC2
  1. git clone down the repo that has your app. For example, I have an app:
  ```bash
  sudo git clone https://github.com/7seven7lst/demo-ec2-nodejs.git
  ```
  2. alternatively, you can also scp a directory into the ec2 instance (if you are using ubuntu instance):
  ```bash
  scp -i <your_PEM_key> -r <your_project_folder>/* ubuntu@e<ec2_public_dns>:/home/ubuntu
  ```
* Install relavent packages needed to run app.
  0. > Note, if you are not using Ubuntu, but some other linux server, you may have "yum" as package manager, instead of "apt-get". In this case, type "sudo yum update", etc....
  1. ```bash
  sudo apt-get update
  ```
  2. ```bash
  sudo apt-get upgrade
  ```
  3. ```bash
  sudo apt-get install nodejs-legacy
  ```
  4. ```bash
  sudo apt-get install npm
  ```
* Deploy App
  1. cd into the app directory
  ```bash
  cd demo-ec2-nodejs # this is the name of my app
  ```
  2. ```bash
  npm install
  ```
  3. ```bash
  node index.js
  ```
* Expose the port
  1. find security group option ![find security group option]({{ site.baseurl }}/images/deploy_ec2/check_security_group.png "find security group option")
  2. choose the security group (should have something "wizard") ![select security group]({{ site.baseurl }}/images/deploy_ec2/select_security_group.png "select security group")
  3. Expose app port to outside ![find inbound config]({{ site.baseurl }}/images/deploy_ec2/find_inbound_config.png "find inbound config") ![expose app port]({{ site.baseurl }}/images/deploy_ec2/expose_app_port.png "expose app port")
* Navigate to the url
  1. copy the url ![copy url]({{ site.baseurl }}/images/deploy_ec2/obtain_app_url.png "copy url")
  2. In brower addres bar, type `<url>:3001` and see the result
* Navigating to observe dashboard chart and coudwatch
  1. dashboard ![ec2 dashboard]({{ site.baseurl }}/images/deploy_ec2/ec2_dashboard.png "ec2 dashboard")
  2. cloudwatch monitoring ![cloudwatch monitoring]({{ site.baseurl }}/images/deploy_ec2/cloudwatch_monitoring.png "cloudwatch monitoring")
* Don't forget to shutdown the EC2 instance
  1. Stop the instance ![shutdown EC2]({{ site.baseurl }}/images/deploy_ec2/shutdown_EC2.png "shutdown EC2")
  2. Terminate the instance
