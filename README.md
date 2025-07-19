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

 

 
 
