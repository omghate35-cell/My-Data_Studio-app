# 🚀 Quick Start Guide

## 1️⃣ Install Dependencies
```bash
pip install -r requirements.txt
```

## 2️⃣ Run Locally
method 1:
```bash
streamlit run streamlit_app.py
```
Your app will open at `http://localhost:8501`

Method 2:
Gui Based 
python "Data Visualation Studio.py"


## 3️⃣ Test Features
- ✅ Upload a CSV or Excel file
- ✅ Preview your data
- ✅ Create multiple chart types
- ✅ Export to PDF
- ✅ Export to PowerPoint

## 4️⃣ Deploy (Pick One)

### Easiest: Streamlit Cloud
1. Push code to GitHub
2. Go to https://streamlit.io/cloud
3. Connect repo and deploy (1 click!)

### Docker Option
```bash
docker build -t data-viz .
docker run -p 8501:8501 data-viz
```

### Heroku Option
```bash
heroku create your-app
git push heroku main
```

---

See **DEPLOYMENT_GUIDE.md** for detailed instructions! 📖
