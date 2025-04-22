# Machine Learning App Deployment on AWS EC2 with Docker

## Overview
This document outlines the steps followed to deploy a machine learning application on an AWS EC2 instance using Docker and Streamlit.

## Prerequisites
- AWS EC2 instance (Amazon Linux 2)
- SSH key pair (`aiml-key.pem`)
- Docker installed on the EC2 instance
- Application files:
  - `Dockerfile`
  - `app.py`
  - `requirements.txt`
  - `mushrooms.csv`

## Steps to Deploy

### 1. Update EC2 Instance
```bash
sudo yum update -y
```

### 2. Install Docker
```bash
sudo amazon-linux-extras install docker
sudo service docker start
```

### 3. Prepare Directory for Application Files
```bash
mkdir downloads
```

### 4. Set Permissions for SSH Key
```bash
chmod 600 aiml-key.pem
```

### 5. Transfer Application Files to EC2
```bash
scp -i ainl-key.pem Dockerfile app.py requirements.txt mushrooms.csv ec2-user@13.60.105.49:/home/ec2-user/downloads
```

### 6. Build Docker Image
```bash
sudo docker build -t my_app:v1.0 -f Dockerfile .
```

### 7. Run Docker Container
```bash
sudo docker run -d -p 8501:8501 my_app:v1.0
```

## Accessing the Application

The application should now be accessible via:
```
http://13.60.105.49:8501
```

## Notes
- Ensure the security group associated with the EC2 instance allows inbound traffic on port 8501.
- If you encounter issues, verify Docker is running and the container is active:
```bash
sudo docker ps
```

## Future Improvements
- Automate deployment with a shell script.
- Implement HTTPS for secure access.
- Set up CI/CD pipeline for continuous deployment.

---
Screenshots
![image](https://github.com/user-attachments/assets/a6c0c48f-e5cc-468e-97b0-240601ccd258)
![image](https://github.com/user-attachments/assets/399fc1af-dbcf-4b3c-8eb8-a7cca69094fa)

*End of README*


