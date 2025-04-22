
# Machine Learning App

This repository contains a machine learning application that can be containerized and run using Docker.

## Prerequisites

Ensure you have the following installed:

- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Setup and Running the Application

### 1. Clone the Repository

```sh
git clone https://github.com/your-username/machine_learning_app.git
cd machine_learning_app
```

### 2. Build the Docker Image

```sh
docker build -t ml_app .
```

### 3. Run the Docker Container

```sh
docker run -p 5000:5000 ml_app
```

This will start the application and expose it on port 5000.

### 4. Using Docker Compose (Alternative)

To run the application using `docker-compose`, execute:

```sh
docker-compose up --build
```

### 5. Access the Application

Once the container is running, open your browser and navigate to:

```
http://localhost:5000
```

### 6. Stopping the Application

- If using `docker run`, stop the container using:
  ```sh
  docker ps  # Find the CONTAINER ID
  docker stop <CONTAINER_ID>
  ```
- If using `docker-compose`, stop the application with:
  ```sh
  docker-compose down
  ```

## Project Structure

```
.
├── Dockerfile
├── docker-compose.yml
├── app.py
├── requirements.txt
├── mushrooms.csv  # Dataset
└── README.md
```
![image](https://github.com/user-attachments/assets/bc6388a6-634a-4464-b55c-e5d120ecabae)

![image](https://github.com/user-attachments/assets/ac0efc42-31d5-4e7a-bab1-1f35fd56dea9)

![image](https://github.com/user-attachments/assets/cda67c71-feb3-49c8-8e08-47f480cc958c)

![image](https://github.com/user-attachments/assets/56da6961-b6a6-419e-a8e9-09671e5c6fc8)

## Contributing

Feel free to open issues or submit pull requests for improvements.
