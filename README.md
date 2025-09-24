# Node.js CI/CD Demo App 🚀

This is a **Node.js + Express.js** demo application deployed via **Docker** and automated **CI/CD pipeline** using **GitHub Actions**, running on **AWS EC2**.

The app shows a **visually appealing page with an image**, and demonstrates a complete DevOps workflow: building, testing, scanning, and deploying automatically.

---

## 🔧 Tools Used

- **GitHub** – Source code management & Actions (CI/CD pipeline)
- **Node.js** – Backend runtime environment
- **Express.js** – Web framework for Node.js
- **Docker** – Containerization of the app
- **Trivy** – Security scanning of Docker images
- **AWS EC2** – Cloud server to host Docker container
- **MobaXterm** – SSH client to access the EC2 instance
- **GitHub Secrets** – Secure storage for DockerHub & EC2 credentials

---

## 📂 Project Structure

nodejs-demo-app/
├── Dockerfile
├── server.js
├── package.json
├── .github/
│ └── workflows/
│ └── main.yml
└── public/
├── index.html
├── style.css
└── image.png


- `server.js` → Express.js server file
- `public/` → HTML, CSS, and image assets
- `Dockerfile` → Docker configuration for app
- `.github/workflows/main.yml` → GitHub Actions CI/CD pipeline

---

## 🚀 Features

- Automatic **CI/CD pipeline**:
  1. Checkout code
  2. Install dependencies
  3. Run tests
  4. Build Docker image
  5. Scan image with Trivy
  6. Push image to DockerHub
  7. Deploy to **AWS EC2**
- **Visually appealing webpage** with image and styled HTML/CSS
- **Automatic rebuild & redeploy** on every push to `main`
- **Docker containerization** for consistent deployment

---

## ⚡ Installation & Running Locally

1. **Clone the repository**
```bash
git clone https://github.com/<your-username>/nodejs-demo-app.git
cd nodejs-demo-app
```

## Install dependencies

npm install

Run locally

node server.js

Open browser:

http://localhost:3000

🐳 Docker Setup

Build Docker image

docker build -t nodejs-demo-app:latest .


Run container

docker run -d -p 3000:3000 --name nodejs-demo-app nodejs-demo-app:latest


Check logs

docker logs nodejs-demo-app

🌐 CI/CD Pipeline (GitHub Actions)

The workflow is defined in .github/workflows/main.yml:

Trigger: push to main branch

Jobs:

Build: installs dependencies, runs tests, builds Docker image

Security Scan: scans image using Trivy

Push: pushes Docker image to DockerHub

Deploy: SSH into EC2, pulls the latest image, restarts container

GitHub Secrets Required:

Secret Name	Description
DOCKER_USERNAME	DockerHub username
DOCKER_PASSWORD	DockerHub password / access token
EC2_HOST	AWS EC2 public IP
EC2_USER	EC2 username (ubuntu or ec2-user)
EC2_SSH_KEY	Private key for EC2 SSH access
🌐 Accessing the App

Once deployed on EC2, open in browser:

http://<EC2-PUBLIC-IP>:3000

You should see the styled page with heading, image, and message confirming deployment via CI/CD.

## ✅ Notes & Best Practices

- The app listens on 0.0.0.0 so Docker can map the port correctly.
- Dockerfile uses caching for npm install to speed up builds.
- Trivy ensures Docker images are scanned for vulnerabilities before deployment.
- GitHub Actions pipeline can be triggered selectively using path filters to avoid unnecessary builds.

## 📸 Screenshot / Demo

<img width="1896" height="878" alt="Screenshot 2025-09-23 223910" src="https://github.com/user-attachments/assets/8d437458-af64-4e8c-bddd-caa1ce0c0eb7" />

<img width="1873" height="769" alt="Screenshot 2025-09-23 223754" src="https://github.com/user-attachments/assets/5adf1a5e-c4a6-482d-80e1-f5c3f0523876" />


