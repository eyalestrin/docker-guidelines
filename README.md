### How to install Docker (Windows Platform)
1. Login to the machine using privileged account
2. Download the latest Docker build from:
	https://download.docker.com/win/edge/Docker%20Desktop%20Installer.exe

### How to install Docker (Ubuntu)
1. Login to the machine using privileged account
2. Follow the instructions below:
	https://docs.docker.com/install/linux/docker-ce/ubuntu/
3. Start the Docker Daemon:  
   `sudo service docker start`

### How to install Docker (RHEL / CentOS)
1. Login to the machine using privileged account
2. Follow the instructions below:  
	https://docs.docker.com/install/linux/docker-ce/centos/

### Install Docker and Docker-compose on Amazon Linux 2
1. Login to the machine using privileged account
2. Run the following commands:  
	`sudo amazon-linux-extras install docker -y`  
	`sudo service docker start`  
	`sudo usermod -a -G docker ec2-user`  
	`sudo chkconfig docker on`  
	`sudo yum install -y git`  
	`sudo curl -L "https://github.com/docker/compose/releases/download/1.22.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose`  
	`sudo chmod +x /usr/local/bin/docker-compose`  
	`sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose`  

### Common Docker commands
+ 	Check the Docker version:  
	`docker --version`
+ Build a docker files using Dockerfile configuration, from the current directory:  
`docker build -t myapp:1.0 -f Dockerfile .`
+ List of all running docker containers:  
`docker ps`  
`docker ps -a`
+ Stop and halt running docker container:  
`docker kill <container_name>`
+ Remove docker container from the local host machine memory/storage:  
`docker rm <container_name>`
+ View logs inside docker container:  
`docker logs <container_name>`
+ Create a docker volume called fs_shared (managed by docker FS):  
`docker volume create fs_shared`
+ Run docker container and mount a volume called fs_shared:  
`docker run --rm -tdi --name alpine1 --mount source=fs_shared,target=/app alpine sh`
+ View list of docker volumes:  
`docker volume ls`
+ Running shell for a remote docker container:  
`docker exec -it <container_name> sh`  
+ Running shell from within a docker container, using port 8080:  
`docker run -d -it --name web_api -p 8080:8080 java:openjdk-8-jre-alpine sh`
+ Running a docker container, mounting local /home/ec2-user/jb_docker/source to /app (inside container), expose port 8080 local to 8080 on container, running the "java:openjdk-8-jre-alpine" image and inside it run the command "java -jar -Dspring.profiles.active=none /app/spring-music.jar":  
`docker run -d -it --name web_api --mount type=bind,source=/home/ec2-user/jb_docker/source,target=/app -p 8080:8080 java:openjdk-8-jre-alpine java -jar -Dspring.profiles.active=none /app/spring-music.jar`
+ Show all network drivers:  
`docker network ls`
+ Create new network bridge called dmz  
`docker network create dmz`
+ Create a docker container with user defined bridge called "dmz"  
`docker run -itd --name alpine1 --network dmz alpine sh`
+ Delete network bridge:  
`docker network prune -f`
+ View information about a container:  
`docker inspect <container_name>`
+ Kill all running docker containers:  
`sudo docker kill $(docker ps -q)`
+ Build and run using docker compose:  
`docker-compose up -d`  
`docker-compose -f docker-compose.yml up -d`
+ Kill existing docker compose (within docker-compose.yml folder):  
`docker-compose down`
+ View logs of docker compose:  
`docker-compose logs -f`
+ View running containers using docker compose:  
`docker-compose ps`  
+ Docker compose clean up:  
`docker-compose rm -f -v -s`
+ Login to Docker registry:  
`docker login`
+ Pulling a docker image from Ducker.hub registry:  
`docker pull alpine:latest`
+ Tagging a docker image:  
`docker tag alpine:latest alpine:1`
+ Pushing a docker image to a registry:  
`docker push alpine:1`
+ Delete all running and unused docker images:  
`docker system prune -a`
