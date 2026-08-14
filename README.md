# DevSecOps CI/CD Pipeline for a Containerized Application  


### Tools

- GitHub
- Jenkins
- Docker
- SonarQube
- OWASP Dependency Check
- Trivy
- AWS EC2



## Pre-requisites to implement this project 

1- AWS ec2 instance(Ubuntu) m5a.large and root volume 27 Gb
2- Install Jenkins
  
3- Docker & Docker Compose installation 
Commands: 
sudo apt-get update
sudo apt-get install docker.io -y
sudo apt-get install docker-compose -y

4- Trivy install
5- SonarQube server install
   docker run -itd --name sonarqube-server -p 9000:9000 sonarqube:lts-community

## Steps for Jenkins CiCd
 Access Jenkins UI and Setup Jenkins
 Install the necessary plugins:  SonarQube scanner
                                 Sonar Quality Gates
                                 OWASP Dependency-check
                                 Docker    
 
 ## All the screenshots of the project is provided in the screeshots folder
 