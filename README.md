
# 🏥 Build-a-Complete-Medical-Chatbot-with-LLMs-LangChain-Pinecone-Flask-AWS

A complete end-to-end **Medical Chatbot** powered by **LLMs (GPT + LangChain)**, vector database (**Pinecone**), and deployed with **Flask** and **AWS CI/CD (GitHub Actions + EC2 + ECR)**.

---

## 🚀 Features

* Conversational **Medical Chatbot** using **LangChain** & **OpenAI GPT**
* Semantic search powered by **Pinecone**
* Flask-based backend for serving requests
* CI/CD pipeline with **GitHub Actions**
* Deployment on **AWS (EC2 + ECR)**

---

## ⚙️ Tech Stack

* **Python**
* **LangChain**
* **Flask**
* **OpenAI GPT**
* **Pinecone**
* **AWS EC2, ECR**
* **GitHub Actions (CI/CD)**

---

## 🛠️ Setup & Installation

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/Raistar22/Medical-chatbot/
cd Medical-Chatbot
```

### 2️⃣ Create Conda Environment

```bash
conda create -n medibot python=3.10 -y
conda activate medibot
```

### 3️⃣ Install Requirements

```bash
pip install -r requirements.txt
```

### 4️⃣ Setup Environment Variables

Create a `.env` file in the **root directory**:

```bash
PINECONE_API_KEY=xxxxxxxxxxxxxxxxxxxxxxxxxxxxx
OPENAI_API_KEY=xxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

### 5️⃣ Store Embeddings to Pinecone

```bash
python store_index.py
```

### 6️⃣ Run the Application

```bash
python app.py
```

Open the app at 👉 **[http://localhost:5000/](http://localhost:5000/)**

---

## ☁️ AWS Deployment

### 1. Login to AWS Console

Create an **IAM User** with these policies:

* `AmazonEC2ContainerRegistryFullAccess`
* `AmazonEC2FullAccess`

### 2. Create an ECR Repository

Example URI:

```
315865595366.dkr.ecr.us-east-1.amazonaws.com/medicalbot
```

### 3. Setup EC2 Machine (Ubuntu)

Install Docker on EC2:

```bash
sudo apt-get update -y
sudo apt-get upgrade -y
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
sudo usermod -aG docker ubuntu
newgrp docker
```

### 4. Configure GitHub Actions Runner

* Go to **Settings > Actions > Runners > New Self-Hosted Runner**
* Choose OS → Run provided commands on EC2

### 5. Setup GitHub Secrets

Add these secrets in your repository:

* `AWS_ACCESS_KEY_ID`
* `AWS_SECRET_ACCESS_KEY`
* `AWS_DEFAULT_REGION`
* `ECR_REPO`
* `PINECONE_API_KEY`
* `OPENAI_API_KEY`

### 6. CI/CD Deployment Steps

1. Build Docker image of source code
2. Push Docker image to **ECR**
3. Launch **EC2**
4. Pull Docker image from **ECR** in EC2
5. Run Docker container on EC2

---

## 📌 Project Workflow

1. User queries chatbot → Flask API
2. Query processed using **LangChain + OpenAI GPT**
3. Vector embeddings retrieved from **Pinecone**
4. Response generated and displayed to user
5. CI/CD ensures continuous deployment to **AWS EC2**

---

## 🧑‍⚕️ Disclaimer

This chatbot is for **educational purposes only**. It is **not a substitute** for professional medical advice. Always consult a healthcare professional for medical concerns.

