# CI/CD Pipeline Demo with Flask, Docker, and GitHub Actions

## Project Overview

This project demonstrates a full CI/CD pipeline using GitHub Actions and Docker. It builds a Flask application, runs tests using pytest, creates a Docker image, pushes it to Docker Hub, and allows you to deploy and run the application locally on an Ubuntu VM.  

Key Features:

- Automated testing with pytest  
- Docker image creation and deployment  
- CI/CD pipeline via GitHub Actions  
- Local deployment without cloud services  

## Project Structure

ci-cd-flask-demo/
├── app.py                  # Flask application
├── requirements.txt        # Python dependencies
├── tests/
│   ├── __init__.py
│   └── test_app.py         # Pytest tests
├── Dockerfile              # Docker image instructions
├── docker-compose.yml      # Optional: run multiple containers locally
├── screenshots/            # Folder containing project screenshots
└── .github/
    └── workflows/
        └── ci-cd.yml       # GitHub Actions workflow



## Setup Instructions

### 1. Clone the repository

git clone https://github.com/YOUR_GITHUB_USERNAME/ci-cd-flask-demo.git
cd ci-cd-flask-demo

### 2. Run tests locally in a virtual environment

# Create and activate virtual environment
python3 -m venv venv
source venv/bin/activate

# Upgrade pip and install dependencies
pip install --upgrade pip
pip install -r requirements.txt

# Run tests
pytest -v

✅ You should see all tests pass:

tests/test_app.py::test_root PASSED

### 3. Build Docker image

docker build -t rahulchembra/ci-cd-flask-demo:latest .

### 4. Run Docker container locally

docker run -d --name ci_demo -p 5000:5000 rahulchembra/ci-cd-flask-demo:latest

- Visit http://localhost:5000/ in your browser 
- You should see:

{"message":"Hello from CI/CD demo!"}

### 5. Stop and remove container

docker stop ci_demo
docker rm ci_demo

## CI/CD Pipeline

- Workflow is defined in .github/workflows/ci-cd.yml  
- Steps executed by GitHub Actions:

1. Checkout code from repo  
2. Set up Python environment  
3. Install dependencies  
4. Run pytest tests  
5. Build Docker image  
6. Push image to Docker Hub  

> If tests fail, the pipeline stops automatically.  

## Dependencies

- Python 3.11  
- Flask 2.2.5  
- pytest 7.2.2  
- Werkzeug < 3.0  
- Docker  

## Docker Hub Image

- Docker image is available at:  
https://hub.docker.com/r/rahulchembra/ci-cd-flask-demo/tags

## Screenshots

- Screenshots of the deployed app and workflow results are included in the **screenshots/ folder**.  
- Please check the folder to see:

  - Deployed app output ({"message":"Hello from CI/CD demo!"})  
  - GitHub Actions workflow success  

## License

This project is open source and available under the MIT License.
