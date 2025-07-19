# Jenkins Hello World CI/CD Pipeline

 Polished Project Summary:
 
This project demonstrates how I installed and configured Jenkins on an AWS EC2 instance and created a basic multi-stage CI/CD pipeline. 
 
--- 
 
##  What I Did 
 
- ✅ Launched a **Free Tier EC2 instance** (Amazon Linux 2) 
- ✅ Configured security groups to allow **SSH (22), HTTP (80), and Jenkins (8080)** traffic 
- ✅ Installed **Java 17** and **Jenkins** manually via CLI 
- ✅ Opened the Jenkins web UI and unlocked it using the initial admin password 
- ✅ Installed suggested plugins and created an admin user 
- ✅ Built a simple CI/CD pipeline using the **Jenkinsfile** 
- ✅ Verified successful builds with console logs from Jenkins stages (Build, Test, Deploy) 
- ✅ Pushed the project files to **GitHub** for portfolio use 
 
--- 
 
## 🧪 Pipeline Overview 
 
This pipeline consists of 3 stages: 
 
```groovy 
pipeline { 
    agent any 
    stages { 
        stage('Build') { 
            steps { 
                echo 'Building...' 
            } 
        } 
        stage('Test') { 
            steps { 
                echo 'Testing...' 
            } 
        } 
        stage('Deploy') { 
            steps { 
                echo 'Deploying Hello World!' 
            } 
        } 
    } 
} 
  

Each stage runs a simple echo command to simulate build, test, and deploy processes. 

 

️ Tools & Technologies Used 

Jenkins 

Amazon EC2 (Amazon Linux 2) 

Git + GitHub 

Linux CLI 

Jenkinsfile (Declarative Pipeline Syntax) 

 

📁 Repo Structure 

jenkins-hello-world/ 
├── Jenkinsfile       # CI/CD pipeline definition 
└── README.md         # Project overview and documentation 
  

 

 

 ✅ Key Takeaways 

Learned how to install and secure Jenkins manually 

Understood how Jenkins Pipelines work using a declarative script 

Connected local Git projects to GitHub for version control 

Practiced EC2 instance management and basic DevOps workflows 

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 Steps to do this lab:
✅ Lab Goal:
Install Jenkins, create a basic “Hello World” CI/CD pipeline, and (if you want) host Jenkins on AWS EC2.
 Tools We'll Use:
Jenkins (self-hosted)


AWS EC2 (Amazon Linux 2)


GitHub (to host your pipeline code)


AWS CLI (optional for tagging/clean-up)



 STEP 1: Launch an EC2 Instance (Free Tier)
We'll run Jenkins on a small t2.micro instance (free tier eligible).
🔹 A. Login to AWS Console → EC2
Go to EC2 > Instances > Launch instance


Name: jenkins-server


AMI: Amazon Linux 2 (x86_64)


Instance type: t2.micro ✅


Key pair: Select or create a key (save .pem file)


Networking: Allow SSH (22), HTTP (80), and custom port 8080 (for Jenkins)


🔹 B. Click Launch → Wait till instance is running

 STEP 2: SSH Into Your EC2 Instance
In terminal or Git Bash:
ssh -i your-key.pem ec2-user@your-public-ip

Replace your-key.pem and IP.

 STEP 3: Install Jenkins on EC2
Run the following commands one by one:
# 1. Install Java (Jenkins needs Java)
sudo dnf install java-17-amazon-corretto -y 
sudo alternatives --config java

# 2. Add Jenkins repo
sudo wget -O /etc/yum.repos.d/jenkins.repo \
  https://pkg.jenkins.io/redhat-stable/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key

# 3. Install Jenkins
sudo yum install jenkins -y

# 4. Start Jenkins
sudo systemctl enable jenkins
sudo systemctl start jenkins

# 5. Allow Jenkins port (8080)
sudo firewall-cmd --permanent --zone=public --add-port=8080/tcp
sudo firewall-cmd --reload


 STEP 4: Access Jenkins Web UI
Go to your browser


Visit: http://<your-ec2-public-ip>:8080


🔑 Unlock Jenkins:
sudo cat /var/lib/jenkins/secrets/initialAdminPassword

Copy the password → paste into browser

✅ Install suggested plugins
 ✅ Create admin user
 ✅ Dashboard loads

⚙️ STEP 5: Create Hello World CI/CD Pipeline
From Jenkins Dashboard:
Click New Item


Name: hello-world-pipeline


Select: Pipeline


Click OK



✏️ Pipeline Script
Scroll down → In "Pipeline" section → choose “Pipeline script” and paste:
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building...'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying Hello World!'
            }
        }
    }
}

✅ Click Save
 ✅ Click Build Now
 📦 Check output logs — you’ll see the echo messages

 
