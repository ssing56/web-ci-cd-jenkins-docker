# Web CI/CD Project using Jenkins & Docker

## Project Overview
This project demonstrates an automated CI/CD pipeline where Jenkins builds and deploys a Dockerized web application whenever code is updated in GitHub.

## Tech Stack
- GitHub
- Jenkins
- Docker
- NGINX
- Ubuntu (AWS EC2)

## CI/CD Flow
1. Code pushed to GitHub
2. Jenkins pipeline triggered
3. Docker image built
4. Old container removed
5. New container deployed automatically

## Application Access
http://<EC2_PUBLIC_IP>:8000
