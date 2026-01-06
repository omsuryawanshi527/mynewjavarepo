Jenkins CI/CD Project using Java on AWS EC2
📌 Project Overview

This project demonstrates how to set up a CI/CD (Continuous Integration & Continuous Deployment) pipeline using Jenkins, Java, GitHub, and Amazon EC2.
Whenever code is pushed to GitHub, Jenkins automatically builds the Java project.

4
🛠️ Technologies Used

AWS EC2 (Linux)

Jenkins

Java

Git & GitHub

Linux (Ubuntu/Amazon Linux)

🎯 Project Objectives

Launch an EC2 server on AWS

Install and configure Jenkins

Create a Java project

Push code to GitHub

Automate build process using Jenkins

🧩 Architecture Flow

Developer pushes Java code to GitHub

GitHub webhook triggers Jenkins

Jenkins pulls the latest code

Jenkins builds the Java project automatically

🔧 Step-by-Step Implementation
1️⃣ Launch EC2 Instance

Create an EC2 instance (Ubuntu / Amazon Linux)

Allow inbound rules:

Port 22 (SSH)

Port 8080 (Jenkins)

2️⃣ Connect to EC2 Server
ssh -i key.pem ubuntu@<EC2-Public-IP>

3️⃣ Install Java
sudo apt update
sudo apt install openjdk-17-jdk -y
java -version

4️⃣ Install Jenkins
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo tee \
/usr/share/keyrings/jenkins-keyring.asc > /dev/null

echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
/etc/apt/sources.list.d/jenkins.list > /dev/null

sudo apt update
sudo apt install jenkins -y
sudo systemctl start jenkins
sudo systemctl enable jenkins

5️⃣ Access Jenkins Dashboard

Open browser:

http://<EC2-Public-IP>:8080


Get initial admin password:

sudo cat /var/lib/jenkins/secrets/initialAdminPassword


Complete Jenkins setup and install suggested plugins

6️⃣ Create Java Project

Example HelloWorld.java:

public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello Jenkins CI/CD Pipeline!");
    }
}

7️⃣ Push Code to GitHub
git init
git add .
git commit -m "Initial Java project"
git branch -M main
git remote add origin https://github.com/username/jenkins-java-project.git
git push -u origin main

8️⃣ Configure Jenkins Job

Create New Item

Select Freestyle Project

Connect GitHub repository

Add build step:

javac HelloWorld.java
java HelloWorld

9️⃣ Automatic Build Trigger

Enable GitHub webhook

Select Build when a change is pushed to GitHub

On every git push, Jenkins builds automatically ✅

✅ Output

Jenkins console shows successful build

Java program runs automatically

CI pipeline works correctly

📌 Key Learnings

Jenkins installation & configuration

Java build automation

GitHub + Jenkins integration

CI/CD fundamentals

AWS EC2 server management

🏁 Conclusion

This project demonstrates a basic but real-world CI/CD pipeline using Jenkins and Java on AWS.
It is suitable for DevOps / Cloud Engineer beginners 
