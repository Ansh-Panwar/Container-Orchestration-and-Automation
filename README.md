# Container-Orchestration-and-Automation
This repository contains different applications made using docker in python programming language.
# Container Orchestration and Automation

## Overview
This repository contains various projects related to container orchestration, Docker, Streamlit applications, database integrations, and Kubernetes configurations. The projects demonstrate how to build and deploy machine learning models, database-backed applications, and microservices using Docker and related technologies.

## Projects
### 1. **Titanic Survival Predictor**
   - Predicts Titanic survival using a trained machine learning model.
   - **Tech Stack:** Streamlit, Docker, Python, Scikit-Learn
   - **Files:**
     - `Dockerfile` - Defines the container environment.
     - `main.py` - Streamlit app for predictions.
     - `titanic_model.pkl` - Pre-trained model.
     - `requirements.txt` - Dependencies.

### 2. **Machine Learning App**
   - A Streamlit-based ML application for classification using a dataset.
   - **Tech Stack:** Python, Streamlit, Docker
   - **Files:**
     - `app.py` - Main application logic.
     - `mushrooms.csv` - Sample dataset.
     - `docker-compose.yml` - Container setup.

### 3. **SQL with Streamlit**
   - Demonstrates database integration with a Streamlit frontend.
   - **Tech Stack:** Python, Streamlit, PostgreSQL, Docker
   - **Files:**
     - `app.py` - Streamlit frontend.
     - `requirements.txt` - Python dependencies.
     - `docker-compose.yml` - Database and application containerization.

### 4. **MySQL Integration**
   - A project demonstrating MySQL database setup in Docker.
   - **Files:**
     - `database_students.sql` - Sample database schema.
     - `Dockerfile` - MySQL setup in a container.

### 5. **Minikube with Docker on Linux**
   - A Kubernetes Minikube setup guide for containerized applications.
   - Includes configuration files and setup instructions.

### 6. **Evidently AI Monitoring**
   - Implements data monitoring using the Evidently AI library.
   - **Files:**
     - `app.py` - Streamlit dashboard for monitoring.
     - `Dockerfile` - Container setup.

## Setup & Deployment
### Prerequisites
- Docker & Docker Compose installed
- Python 3.7+
- Streamlit installed

### Running a Project
1. Clone the repository:
   ```sh
   git clone https://github.com/your-repo/Container-Orchestration-and-Automation.git
   cd Container-Orchestration-and-Automation
   ```
2. Navigate to a specific project folder (e.g., `Titanic_Survival_Predictor`).
3. Build and run the container:
   ```sh
   docker-compose up --build
   ```
4. Access the application at `http://localhost:8501`



## Contributing
Contributions are welcome! Feel free to submit issues or pull requests.


