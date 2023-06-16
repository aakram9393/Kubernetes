#How to push a Docker image to a private docker registery

First step get the IAM user AK/SK from the AWS console

Retrieve an authentication token and authenticate your Docker client to your registry.
Use AWS Tools for PowerShell:

(Get-ECRLoginCommand).Password | docker login --username AWS --password-stdin 776538664207.dkr.ecr.us-east-1.amazonaws.com
Build your Docker image using the following command. For information on building a Docker file from scratch see the instructions here . You can skip this step if your image is already built:

docker build -t my-app .
After the build completes, tag your image so you can push the image to this repository:

docker tag my-app:latest 776538664207.dkr.ecr.us-east-1.amazonaws.com/my-app:latest
Run the following command to push this image to your newly created AWS repository:

docker push 776538664207.dkr.ecr.us-east-1.amazonaws.com/my-app:latest
-----------

docker login -u AWS -p <ecr-private-repo-password>