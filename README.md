# In this CI-CD_Pipeline_Project, I will use these tools: #
1. Jenkins
2. Git Hub
3. Maven
4. Docker

# (1) Jenkins Server Setup in Linux VM #

1) Create Ubuntu VM using AWS EC2 (t2.medium)
2) Enable 8080 Port Number in Security Group Inbound Rules
3) Connect to VM using MobaXterm
4) Install Java


```
sudo apt update
sudo apt install fontconfig openjdk-17-jre
java -version
```

5) Install Jenkins
```
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins
```
6) Start Jenkins

```
sudo systemctl enable jenkins
sudo systemctl start jenkins
```

7) Verify Jenkins

```
sudo systemctl status jenkins
```
	
8) Access jenkins server in browser using VM public ip

```
http://public-ip:8080/

```

9) Copy jenkins admin pwd

```
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```
	   
10) Create Admin Account & Install Required Plugins in Jenkins

# (2) Configure Maven as Global Tool in Jenkins #

1) Manage Jenkins -> Tools -> Maven Installation -> Add maven <br/>

# (3) Setup Docker in Jenkins #
```
curl -fsSL get.docker.com | /bin/bash
sudo usermod -aG docker jenkins
sudo usermod -aG docker ubuntu
sudo systemctl restart jenkins
sudo docker version
```

# (4) Create Jenkins Job #

- **Stage-1 : Clone Git Repo** <br/> 
- **Stage-2 : Maven Build** <br/>
- **Stage-3 : Create Docker Image** <br/>
- **Stage-4 : Create Docker Container** <br/>
	
# (5) Trigger Jenkins Job #

# (6) Enable host port in security group inbound rules #

# (7) Access Application in Browser #

- **We should be able to access our application** <br/>

URL : http://public-ip:port/
	
# We are done with our Setup #
	
# (8) After the practise, delete resources we have used in AWS Cloud to avoid billing #