# DevSecOps-Project
Phase 1: Initial Setup and Deployment
Step 1: Launch EC2 (Ubuntu 22.04):

Provision an EC2 instance on AWS with Ubuntu 22.04.
Connect to the instance using SSH.

----------------------------------------------------------->

Step 2: Clone the Code:

Update all the packages and then clone the code.

Clone your application's code repository onto the EC2 instance

----------------------------------------------------------->

Step 3: Install Docker and Run the App Using a Container:

Set up Docker on the EC2 instance:

sudo apt-get update
sudo apt-get install docker.io -y
sudo usermod -aG docker $USER  # Replace with your system's username, e.g., 'ubuntu'
newgrp docker
sudo chmod 777 /var/run/docker.sock

---------------------------------------------------------->

Step 4
Build and run your application using Docker containers

docker build -t netflix .
docker run -d --name netflix -p 8081:80 netflix:latest

#to delete
docker stop <containerid>
docker rmi -f netflix

------------------------------------------------------------>

Step 5
Open a web browser and navigate to TMDB (The Movie Database) website.
Click on "Login" and create an account.
Once logged in, go to your profile and select "Settings."
Click on "API" from the left-side panel.
Create a new API key by clicking "Create" and accepting the terms and conditions.
Provide the required basic details and click "Submit."
You will receive your TMDB API key.
Now recreate the Docker image with your api key:

docker build --build-arg TMDB_V3_API_KEY=<your-api-key> -t netflix .

------------------------------------------------------------>
