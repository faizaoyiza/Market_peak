# Market_peak

## Project Overview
This project demonstrates the deployment of an e-commerce website called **MarketPeak** using Git for version control, Linux for the development environment, and AWS EC2 for hosting. The platform features product listings, a shopping cart, and user authentication.

## Technologies Used
- Git & GitHub
- Linux (Amazon Linux 2)
- Apache HTTP Server (httpd)
- AWS EC2

---

## 1. Version Control with Git

### 1.1 Initialize Git Repository
```bash
mkdir MarketPeak_Ecommerce
cd MarketPeak_Ecommerce
git init
```

### 1.2 Add Website Template
- Download a free e-commerce template (e.g., from Tooplate).
- Extract contents into `MarketPeak_Ecommerce` directory.

### 1.3 Stage & Commit Files
```bash
git config --global user.name "yourname"
git config --global user.email "youremail@example.com"
git add .
git commit -m "Initial commit with basic e-commerce site structure"
```

### 1.4 Push to GitHub
```bash
git remote add origin https://github.com/yourusername/MarketPeak_Ecommerce.git
git push -u origin main
```

---

## 2. AWS Deployment

### 2.1 Launch EC2 Instance
- Use Amazon Linux AMI
- Connect using SSH

### 2.2 Clone Repository
#### SSH Method
```bash
ssh-keygen
cat ~/.ssh/id_rsa.pub  # Add to GitHub SSH keys
git clone git@github.com:yourusername/MarketPeak_Ecommerce.git
```

#### HTTPS Method
```bash
git clone https://github.com/yourusername/MarketPeak_Ecommerce.git
```

### 2.3 Install Apache (httpd)
```bash
sudo yum update -y
sudo yum install httpd -y
sudo systemctl start httpd
sudo systemctl enable httpd
```

### 2.4 Configure Web Directory
```bash
sudo rm -rf /var/www/html/*
sudo cp -r ~/MarketPeak_Ecommerce/* /var/www/html/
sudo systemctl reload httpd
```

### 2.5 Access Site
- Open browser: `http://<your-ec2-public-ip>`

---

## 3. CI/CD Workflow

### Step 1: Create Development Branch
```bash
git branch development
git checkout development
```

### Step 2: Commit Changes
```bash
git add .
git commit -m "Feature or bug fix description"
git push origin development
```

### Step 3: Merge to Main via Pull Request on GitHub

### Step 4: Deploy from Main Branch
```bash
ssh into EC2
cd /var/www/html/
git pull origin main
sudo systemctl reload httpd
```

### Step 5: Test Website

---

## 4. Capstone Submission

### 4.1 Document the Process
- Include this README.md in your GitHub repository.

### 4.2 Share GitHub Repo
- Submit the link to your GitHub repo on darey.io

---

## Troubleshooting

- **Permission denied (publickey)**: Add your SSH key to GitHub.
- **Apache not serving updated site**: Check `/var/www/html` and restart Apache.
- **403 Forbidden**: Check file permissions and ownership.

---

## Useful Git Commands
```bash
git status
git log
git branch -a
git pull origin branch_name
git push origin branch_name
```

---

## Author
MarketPeak Deployment Team - Capstone Project
