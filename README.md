<p align="center">
<img src="https://github.com/kura-labs-org/kuralabs_deployment_1/blob/main/Kuralogo.png">
</p>
<h1 align="center">C4_deployment-2<h1> 


### 🎯 Objective

Demonstrate the ability to run a Jenkins build and manually deploy to Elastic Beanstalk.

🔍 **Why?**  
Our project's aim is to build, test, and deploy a URL-shortener application using Jenkins, orchestrated through GitHub. This serves as a practical example to test and verify our DevOps capabilities.

---

### 🚀 Phase 1: Setup 

1. **Download the Repository**  
   - 📝 To start, I downloaded the repository found at [this link](https://github.com/kura-labs-org/kuralabs_deployment_2).

2. **Unzip and Upload to GitHub**  
   - 🗂 After downloading the Zip file, I extracted the contents and uploaded them into my own GitHub repository.

🔍 **Why?**  
The repository contains the base code needed for the URL-shortener. By forking it into our own GitHub, we make it easier to manage version control and enable integration with Jenkins.

---

### 🛠 Phase 2: EC2 and Jenkins Setup

1. **EC2 Instance Setup**
   - 🖥 I set up a brand new EC2 instance following the instructor's specifications.

2. **Install Dependencies**
   - 🐍 Download Python, 🛠 Jenkins, and 🔌 install the Jenkins plugin "Pipeline Utility Steps".

🔍 **Why?**
- EC2: We need a virtual machine to host Jenkins and run our build.
- Python: The URL-shortener application is Python-based.
- Jenkins and Plugin: These are essential for automating our build and deployment process.

3. **Check Python Version**  
   - ```python3 --version```

4. **Update Packages and Python Dependencies**
   - ```sudo apt update```
   - ```sudo apt install python3.10-venv```

🔍 **Why?**  
- Checking Python versions ensures compatibility.
- Updating packages reduces vulnerabilities and ensures we have the latest features and fixes.

5. **Java Package Installation**  
   - ```sudo apt-get install fontconfig openjdk-17-jre```

6. **Jenkins Installation**
   - Use the following BASH commands to install Jenkins.
     ```bash
     curl -fsSL https://pkg.jenkins.io/debian/jenkins.io-2023.key | sudo tee /usr/share/keyrings/jenkins-keyring.asc > /dev/null
     echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] tps://pkg.jenkins.io/debian binary/ | sudo tee tc/apt/sources.list.d/jenkins.list > /dev/null
     sudo apt update
     sudo apt-get install jenkins
     sudo systemctl start jenkins
     sudo systemctl status jenkins
     ```

7. **Install Jenkins Plugin**
   - 📦 Once installed, go to Jenkins and add the "Pipeline Utility Settings" plugin.

8. **Token for Authentication**
   - 🛡 Create a personal web token to secure your build process.

9. **Run and Test the Build**
   - 🏃‍♂️ Use the SCM script in Jenkins to run the build.
   - 🧪 Test the build; Jenkins will create a zip file in a specific directory. 
   - 🔍 Use `sudo cat` to check the file.

🔍 **Why?**
- Java: Jenkins requires Java as a dependency.
- Jenkins Installation: Necessary for build automation.
- Plugin: Adds utility steps to our pipeline.
- Token: Ensures that only authorized personnel can execute builds.

### 📦 Phase 3: Transferring Zip File and Elastic Beanstalk Setup

This phase deals with transferring the built zip file from the EC2 instance to your local directory and setting up the deployment environment on Elastic Beanstalk.

#### Step 1: SSH Key Preparation
- 🗝 Use the command line to fetch the SSH key from your local device.
- 🖥 Paste this SSH key into the authentication section of your EC2 instance.

🔍 **Why?**  
SSH keys provide a secure way of logging into your EC2 instance without requiring a password. This enables a secure data transfer between your local machine and the EC2 instance.

#### Step 2: Secure Copy Protocol (SCP) to Transfer File
- 📥 Use SCP to download the zip file from your remote server (EC2 instance) to your local computer.
  ```bash
  scp ubuntu@insert_ip_address_here:insert_absolute_directory_path_here/insert_file_name_here_including_extension .
  ```

🔍 **Why?**  
The SCP command allows you to securely copy files between the local host and the remote host or between two remote hosts. By using SCP, you ensure that the file transfer occurs over a secure channel.

#### Step 3: Setup IAM Roles
- 🛡 Configure Identity and Access Management (IAM) roles for your project.

🔍 **Why?**  
IAM roles are a secure way to delegate permissions that doesn't involve sharing security credentials. They are essential for Elastic Beanstalk to interact with other AWS services on your behalf.

#### Step 4: Elastic Beanstalk Setup
- 🌱 Initialize and set up Elastic Beanstalk environment and application settings according to your project's requirements.

🔍 **Why?**  
Elastic Beanstalk offers a platform where you can easily deploy applications. Setting it up properly will ensure that the platform can handle your application with auto-scaling, load balancing, and more, without you having to manage the underlying instances.

---
![Screenshot 2023-08-25 at 11 57 30 PM](https://github.com/jaganzen/c4_deployment2/assets/101806502/72a5c51c-2f2f-472b-a987-1dc024dc95de)

![Screenshot 2023-08-25 at 11 58 12 PM](https://github.com/jaganzen/c4_deployment2/assets/101806502/194dbdde-48f8-411e-afd5-478c824a003e)

---

