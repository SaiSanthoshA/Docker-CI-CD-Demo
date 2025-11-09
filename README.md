🐳 Docker CI/CD Demo – Automated Build & Deployment
🚀 Overview

This project demonstrates how to automate Docker image builds and deployments using GitHub Actions.
Every time new code is pushed to the main branch, a GitHub Actions workflow automatically:

Builds a Docker image from the Dockerfile

Pushes it to the GitHub Container Registry (GHCR)

🧩 Features

🐍 Flask-based Python web app

🧱 Dockerized application

⚙️ Automated CI/CD pipeline using GitHub Actions

🔐 Secure image upload using GITHUB_TOKEN

📂 Project Structure
docker-ci-cd-demo/
├── app.py
├── Dockerfile
└── .github/
    └── workflows/
        └── docker-build.yml

⚙️ Workflow Logic
name: Build and Push Docker Image

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Log in to GitHub Container Registry
        uses: docker/login-action@v3
        with:
          registry: ghcr.io
          username: ${{ github.actor }}
          password: ${{ secrets.GITHUB_TOKEN }}

      - name: Build Docker image
        run: docker build -t ghcr.io/${{ github.repository }}:latest .

      - name: Push Docker image
        run: docker push ghcr.io/${{ github.repository }}:latest

🧠 How to Run the Image

After the workflow runs successfully, pull and run the image:

docker pull ghcr.io/<your-username>/docker-ci-cd-demo:latest
docker run -p 5000:5000 ghcr.io/<your-username>/docker-ci-cd-demo:latest


Visit http://localhost:5000
 in your browser to see:

Automated Docker Build Successful!

🏆 Tech Stack

Python 3.10

Flask

Docker

GitHub Actions

✨ Author

👨‍💻 Sai Santhosh A
🎓 Cybersecurity Student | 🌐 Aspiring DevOps Engineer
🔗 LinkedIn Profile
 (you can replace with your link)
