### How to install Docker (Windows Platform)
1. Login to the machine using privileged account
2. Download the latest Docker build from:
: https://download.docker.com/win/edge/Docker%20Desktop%20Installer.exe

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
