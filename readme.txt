This is an energy management system developed during the distributed system course.

# Project Runs on http://localhost:3003

#======================== RUN PROJECT ==========================

# To run the whole project, we will use the docker-compose.yml in the root directory:
sudo docker compose up

#===================== RUNNING TRANSMITTER =====================

# Navigate to root directory and run:
python3 transmitter.py <UUID of a device or nothing>

#===============================================================

#If you want to run each service serparately:

# Remove any previous containers or images - use 'sudo" if on linux! if not remove "sudo" and all appearances!
sudo docker ps -q | xargs -r sudo docker rm -f && sudo docker image ls -q | xargs -r sudo docker rmi -f

# build the user microservice container:
sudo docker build . -t users-service --no-cache && sudo docker compose up --remove-orphans

# build the chat microservice container:
sudo docker build . -t chat-service --no-cache && sudo docker compose up --remove-orphans

# build the device microservice container:
sudo docker build . -t devices-service --no-cache && sudo docker compose up --remove-orphans

# build the frontend container:
sudo docker build . -t frontend --no-cache && sudo docker compose up --remove-orphans

# build the reciever microservice container:
sudo docker build . -t reciever-service --no-cache && sudo docker compose up --remove-orphans

#================================================================
