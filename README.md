# DevOps Intern Final Assessment

[![CI](https://github.com/gitamoo/devops-intern-final/actions/workflows/ci.yml/badge.svg)](https://github.com/gitamoo/devops-intern-final/actions/workflows/ci.yml)

**Name:** Rita Gitamo  
**Date:** July 10, 2026

---

## Project Description

This repository demonstrates a complete DevOps workflow using open-source tools and cloud-native practices. The project covers version control, Linux scripting, containerization, continuous integration, workload orchestration, and monitoring.

The technologies used include:

- Git & GitHub
- Linux (Bash)
- Docker
- GitHub Actions
- Nomad
- Grafana Loki

Each section builds on the previous one to simulate a simple but realistic DevOps pipeline.

---

## Repository Structure

```text
devops-intern-final/
│
├── .github/
│   └── workflows/
│       └── ci.yml
│
├── monitoring/
│   └── loki_setup.txt
│
├── nomad/
│   └── hello.nomad
│
├── scripts/
│   └── sysinfo.sh
│
├── Dockerfile
├── hello.py
├── README.md
└── screenshots/
```

---

# Step 1: Git & GitHub Setup

A public GitHub repository was created and initialized using Git.

### Files Created

- `README.md`
- `hello.py`

### `hello.py`

```python
print("Hello, DevOps!")
```

### Run the Application

```bash
python3 hello.py
```

### Expected Output

```text
Hello, DevOps!
```

---

# Step 2: Linux Scripting Basics

A Bash script was created to display basic system information.

### File

`scripts/sysinfo.sh`

### Script Functionality

The script displays:

- Current user
- Current date and time
- Disk usage

### Make the Script Executable

```bash
chmod +x scripts/sysinfo.sh
```

### Execute the Script

```bash
./scripts/sysinfo.sh
```

### Sample Output

```text
Current User:
kerubo

Current Date:
Fri Jul 10 ...

Disk Usage:
Filesystem      Size Used Avail Use%
...
```

---

# Step 3: Docker Containerization

A Docker image was created to containerize the Python application.

### Dockerfile

```dockerfile
FROM python:3.12-slim

WORKDIR /app

COPY hello.py .

CMD ["python", "hello.py"]
```

### Build the Image

```bash
docker build -t hello-devops .
```

### Run the Container

```bash
docker run hello-devops
```

### Expected Output

```text
Hello, DevOps!
```

---

# Step 4: Continuous Integration with GitHub Actions

GitHub Actions is configured to automatically run the application whenever code is pushed to the `main` branch.

### Workflow File

```
.github/workflows/ci.yml
```

### Workflow Steps

1. Check out the repository.
2. Set up Python.
3. Execute `hello.py`.
4. Verify successful execution.

### Trigger

The workflow runs automatically whenever changes are pushed to the `main` branch.

### Status Badge

The badge at the top of this README displays the latest workflow status.

- 🟢 **Passing** – The workflow completed successfully.
- 🔴 **Failing** – One or more workflow steps failed.

Click the badge to view detailed workflow logs.

---

# Step 5: Nomad Deployment

A Nomad job specification was created to deploy the Docker container.

### File

```
nomad/hello.nomad
```

### Job Configuration

- **Type:** `service`
- **Driver:** Docker
- **CPU:** 100 MHz
- **Memory:** 128 MB

### Deploy the Job

```bash
nomad job run nomad/hello.nomad
```

### Verify Deployment

```bash
nomad job status hello
```

---

# Step 6: Monitoring with Grafana Loki

Grafana Loki is used for centralized log collection.

### Documentation

```
monitoring/loki_setup.txt
```

### Start Loki

```bash
docker run -d \
  --name=loki \
  -p 3100:3100 \
  grafana/loki:latest
```

### View Container Logs

```bash
docker logs loki
```

### Verify Loki is Running

```bash
curl http://localhost:3100/ready
```

If Grafana is installed, add Loki as a data source and view logs through the **Explore** page.

---

# Continuous Integration Workflow

The CI pipeline automatically validates the application whenever code is pushed to GitHub.

### Workflow Process

1. A commit is pushed to GitHub.
2. GitHub Actions starts automatically.
3. The repository is checked out.
4. Python is installed.
5. `hello.py` is executed.
6. The workflow reports success or failure.

This ensures that every code change is automatically tested before further deployment.

---

# Technologies Used

| Technology | Purpose |
|------------|---------|
| Git | Version control |
| GitHub | Source code hosting |
| Linux | Operating system and command-line tools |
| Bash | System scripting |
| Docker | Application containerization |
| GitHub Actions | Continuous Integration |
| Nomad | Workload orchestration |
| Grafana Loki | Centralized logging |
| Python | Sample application |

---

# Running the Project

## Clone the Repository

```bash
git clone https://github.com/gitamoo/devops-intern-final.git
cd devops-intern-final
```

## Run the Python Application

```bash
python3 hello.py
```

## Run the Linux Script

```bash
chmod +x scripts/sysinfo.sh
./scripts/sysinfo.sh
```

## Build the Docker Image

```bash
docker build -t hello-devops .
```

## Run the Docker Container

```bash
docker run hello-devops
```

## Deploy Using Nomad

```bash
nomad job run nomad/hello.nomad
```

## Verify the CI Pipeline

Push a change to GitHub:

```bash
git add .
git commit -m "Test GitHub Actions"
git push origin main
```

Then navigate to the **Actions** tab in the GitHub repository to verify that the workflow completed successfully.

---

# Screenshots

This repository may include screenshots demonstrating:

- Successful GitHub Actions workflow
- Docker container output
- Nomad deployment
- Grafana Loki setup (optional)

---

# Learning Outcomes

This project demonstrates practical experience with:

- Git and GitHub
- Linux command-line usage
- Bash scripting
- Docker containerization
- Continuous Integration with GitHub Actions
- Nomad workload deployment
- Grafana Loki log monitoring
- Technical documentation and project organization

---

# Author

**Rita Gitamo**

DevOps Intern Final Assessment

July 2026
