# 🧪 Simple Python Application with Jenkins CI/CD Pipeline

![Jenkins Logo](https://www.jenkins.io/images/logos/jenkins/jenkins.png)

## 📌 Project Overview

This project demonstrates a simple Python application integrated with a complete CI/CD pipeline using **Jenkins**, **Docker**, and **GitHub**.  
The application is a command-line tool that adds two numbers together. The project features:

- Automated testing
- Continuous Integration/Deployment using Jenkins
- Dockerized build and testing environments

> ⚠️ **Note**: Ensure Docker Desktop is running before executing any Docker-related commands.

---

## 🧩 Project Structure

```
.
├── sources/
│   ├── add2vals.py        # Main CLI application
│   ├── calc.py            # Core logic (addition)
│   └── test_calc.py       # Unit tests
├── dist/                  # Generated executables
├── requirements.txt       # Python dependencies
├── Jenkinsfile            # CI/CD pipeline configuration
├── docker-compose.yml     # Docker environment for Jenkins
└── README.md              # Project documentation
```

---

## 🐍 Python Application

- **`add2vals.py`**: Entry point that handles CLI input and displays results.
- **`calc.py`**: Contains the logic for adding two numbers.
- **`test_calc.py`**: Unit tests for the `calc` module.
- **`requirements.txt`**: Python packages required for the application.

---

## ⚙️ CI/CD Pipeline with Jenkins

### 🔧 Jenkins Configuration

- **Jenkinsfile**: Defines the CI/CD workflow (build, test, package).
- **docker-compose.yml**: Spins up Jenkins server and agent containers with required volumes and networks.

### 🐳 Docker Containers

- **Jenkins Server**: Main CI/CD orchestrator with persistent storage.
- **Jenkins Agent**: Handles builds and job execution.
- **Python Build Container**: Used to build and test the Python app.

---

## 🚀 Getting Started

### Step 1: Setup Jenkins

Start Jenkins using Docker Compose:
```bash
docker-compose up -d
```

Get the initial admin password:
```bash
docker-compose exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword
```

Access Jenkins in your browser:  
`http://localhost:8080`

Complete the setup:
- Install suggested plugins
- Create the first admin user
- Keep the default Jenkins URL

### Step 2: Create the Pipeline Project

1. Click **"New Item"**
2. Name the project: `simple-python-pyinstaller-app`
3. Choose **"Pipeline"**, click **OK**
4. Under **Pipeline script from SCM**:
   - SCM: `Git`
   - Repository URL: `https://github.com/TarakKatoch/Jenkins-Orchestration.git`
   - Branch: `*/master`

Click **Save**

### Step 3: Configure Docker Inside Jenkins

Install Docker inside Jenkins container:
```bash
docker-compose exec jenkins bash -c "apt-get update && apt-get install -y docker.io"
docker-compose exec jenkins bash -c "service docker start"
docker-compose exec jenkins docker --version
```

Install required Docker plugins in Jenkins:
- Docker Pipeline
- Docker plugin
- docker-build-step

Restart Jenkins:
```bash
docker-compose restart jenkins
```

---

## ▶️ Running the Pipeline

1. Go to the pipeline project in Jenkins
2. Click **"Build Now"**
3. After the build completes, download the executable from **Build Artifacts**

---

## 💻 Running the Executable

> The generated executable is a Linux binary.

To run on Windows, use **WSL** (Windows Subsystem for Linux):

### Setup WSL

```bash
wsl --version
# If WSL is not installed:
wsl --install
```

### Run the Executable in WSL

```bash
wsl
cd /mnt/c/Users/<your-user>/Downloads
chmod +x add2vals
./add2vals 5 3
```

---

## 📦 What Does PyInstaller Do?

**PyInstaller** converts Python scripts into standalone executables.

### ✅ Process

- **Analysis**: Scans source files and dependencies
- **Bundling**: Packages everything including Python interpreter
- **Output**: Generates an executable in `dist/`

### ✅ Benefits

- **Portability**: Single-file executable
- **No Dependencies**: No need to install Python
- **Cross-Platform**: Works on Windows, Linux, macOS
- **Consistency**: Same behavior across environments

---

## ✅ Conclusion

This project showcases a complete CI/CD pipeline using:

- Jenkins for automation
- Docker for containerization
- PyInstaller for building portable executables

### 💡 What You’ve Learned

- How to set up a Jenkins server with Docker
- How to automate build, test, and deployment pipelines
- How to use PyInstaller to package Python apps

---

## 🙌 Thank You!

If you found this helpful:

- ⭐ Star this repo
- 🔁 Share with others
- 🛠️ Contribute improvements or suggestions
- 🐞 Report any issues

**Happy Coding! 🚀**
