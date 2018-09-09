---
layout: post
title: Deploy NodeJS App to AWS EC2!
---

Deploy NodeJS App to AWS EC2.

1. Create EC2 Instance
  a. Click EC2
  b. Filter "Free Tier Only"
  c. Select "Ubuntu"
  d. Select "t2.micro (free tier)"
  e. launch instance
2. Generate a Key file and download it
3. SSH into the EC2 instance with your key file
  a. open terminal
  b. cd into the directory that has the key you downloaded.
4. Clone down the app into EC2
  a. sudo git clone https://github.com/7seven7lst/demo-ec2-nodejs.git
5. Install relavent packages needed to run app.
  a. apt-get update
  b. apt-get upgrade
  c. apt-get install nodejs-legacy
  d. apt-get install npm
6. Deploy App
  a. cd into the app directory
  b. npm install
  c. node index.js 
7. Expose the port
  a. 
8. Navigate to the url
  a. copy the url
  b. type <url>:3001 and see the result
9. Don't forget to shutdown the EC2 instance
  a. Stop the instance
  b. Terminate the instance
