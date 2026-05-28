# 🚀 Deployment Guide - Data Visualization Studio

## 📋 Prerequisites
- Python 3.8+
- Git account (for Streamlit Cloud)

---

## 🎯 OPTION 1: Deploy to Streamlit Cloud (RECOMMENDED - Easiest)

### Step 1: Install Streamlit Locally
```bash
pip install -r requirements.txt
```

### Step 2: Test Your App Locally
```bash
streamlit run streamlit_app.py
```
Visit `http://localhost:8501`

### Step 3: Push to GitHub
1. Create a GitHub repository
2. Push your files:
```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git
git push -u origin main
```

### Step 4: Deploy on Streamlit Cloud
1. Go to https://streamlit.io/cloud
2. Click "New App"
3. Select your GitHub repo, branch, and file (`streamlit_app.py`)
4. Deploy!

**Your app will be live at:** `https://YOUR_USERNAME-YOUR_REPO.streamlit.app`

---

## 🐳 OPTION 2: Deploy with Docker (for VPS/AWS/DigitalOcean)

### Create Dockerfile
```dockerfile
FROM python:3.11-slim

WORKDIR /app

COPY requirements.txt .
RUN pip install -r requirements.txt

COPY . .

EXPOSE 8501

CMD ["streamlit", "run", "streamlit_app.py", "--server.port=8501", "--server.address=0.0.0.0"]
```

### Build & Run Locally
```bash
docker build -t data-viz-studio .
docker run -p 8501:8501 data-viz-studio
```

### Deploy to Cloud
**AWS EC2:**
```bash
docker build -t data-viz-studio .
docker tag data-viz-studio:latest YOUR_AWS_ACCOUNT.dkr.ecr.us-east-1.amazonaws.com/data-viz-studio
docker push YOUR_AWS_ACCOUNT.dkr.ecr.us-east-1.amazonaws.com/data-viz-studio
```

---

## 🚀 OPTION 3: Deploy to Heroku

### Step 1: Create Procfile
```
web: streamlit run streamlit_app.py --server.port=$PORT --server.address=0.0.0.0
```

### Step 2: Create setup.sh
```bash
mkdir -p ~/.streamlit/
echo "[browser]
headless = true

[server]
port = $PORT
enableXsrfProtection = false
enableCORS = false
" > ~/.streamlit/config.toml
```

### Step 3: Deploy
```bash
heroku login
heroku create YOUR_APP_NAME
git push heroku main
```

---

## 📊 OPTION 4: Deploy to PythonAnywhere

1. Sign up at https://www.pythonanywhere.com/
2. Upload your files
3. Create a Web App
4. Configure Python 3.11 + WSGI
5. Install dependencies via bash console

---

## 🔧 Local Development Commands

**Install dependencies:**
```bash
pip install -r requirements.txt
```

**Run app:**
```bash
streamlit run streamlit_app.py
```

**Access:**
Open http://localhost:8501

---

## 📦 Project Structure
```
My Project's/
├── streamlit_app.py      # Main Streamlit app
├── requirements.txt      # Python dependencies
├── Dockerfile           # For Docker deployment
├── Procfile             # For Heroku deployment
└── setup.sh             # Setup script for Heroku
```

---

## ⚡ Features
✅ Upload CSV/Excel files  
✅ Data preview & statistics  
✅ 7+ chart types (bar, line, pie, histogram, scatter, box, area)  
✅ Export to PDF  
✅ Export to PowerPoint  
✅ Real-time visualization  

---

## 🆘 Troubleshooting

**Port already in use?**
```bash
streamlit run streamlit_app.py --server.port=8502
```

**Dependencies not installing?**
```bash
pip install --upgrade pip
pip install -r requirements.txt --force-reinstall
```

**App crashes after upload?**
Check file size (max 200MB on Streamlit Cloud), ensure data is in UTF-8 encoding

---

## 🎯 Recommended Deployment Path
**For Beginners:** Streamlit Cloud (1-click deploy)  
**For Production:** Docker + AWS/DigitalOcean  
**For Testing:** PythonAnywhere or Heroku
