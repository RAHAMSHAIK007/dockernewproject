DOCKER PROJECT:


yum install docker -y
systemctl start docker
systemctl status docker

FROM ubuntu
RUN apt-get update -y
RUN apt-get install apache2 -y
COPY index.html /var/www/html/
CMD ["/usr/sbin/apachectl", "-D", "FOREGROUND"]



DOCKER FILE	: To create image by automation.
DOCKER COMPOSE	: To create multiple containers on single server.
DOCKER SWARM	: To create multiple containers on Multiple server.
DOCKE STACK	: Docker swarm + Docker compose

1. CREATE 3 SERVERS AND INSTALL DOCKER ON ALL OF THEM & CREATE CLUSTER OF IT

yum install docker -y
systemctl start docker
systemctl status docker
docker swarm init --advertise-addr 172.31.85.110
docker node ls


2. INSTALLING JENKINS (MASTER)

sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
amazon-linux-extras install java-openjdk11 -y 
yum install git maven jenkins -y
systemctl start jenkins.service
systemctl status jenkins.service


3. CREATE CUSTOM IMAGES AND PUSH TO DOCKERHUB WITH TAGS

DOCKER FILE:
FROM ubuntu
RUN apt-get update -y
RUN apt-get install apache2 -y
COPY index.html /var/www/html/
CMD ["/usr/sbin/apachectl", "-D", "FOREGROUND"]

INDEX.HTML:


PIPELINE:

pipeline {
    agent any 
    
    stages {
        stage('checkout') {
            steps {
                git 'https://github.com/RAHAMSHAIK007/dockernewproject.git'
            }
        }
        stage('build') {
            steps {
                sh 'docker build -t $img .'
            }
        }
        stage('tag') {
            steps {
                sh 'docker tag $img $repo'
            }
        }
        stage('push') {
            steps {
                sh 'docker login -u  -p '
                sh 'docker push $repo'
            }
        }
    }
}


4. GIVE PERMISSIONS

chmod 777 /var/run/docker.sock
systemctl daemon-reload
systemctl restart docker.service


5. WRITE COMPOSE FILE AND PUSH TO GITHUB

version: '3'
services:
  devops:
    image: rahamshaik/devopsreponit:latest
    ports:
      - "80:80"
    volumes:
      - "devopsvol"
    deploy:
      replicas: 3

  aws:
    image: rahamshaik/awsreponit:latest
    ports:
      - "81:80"
    volumes:
      - "awsvol"
    deploy:
      replicas: 3

  datascience:
    image: rahamshaik/datasciencereponit:latest
    ports:
      - "82:80"
    volumes:
      - "datasciencevol"
    deploy:
      replicas: 3

  azure:
    image: rahamshaik/azurereponit:latest
    ports:
      - "83:80"
    volumes:
      - "azurevol"
    deploy:
      replicas: 3
