<h1 align="center">Hi 👋, I'm Dzaky</h1>
<h3 align="center">A passionate Data Analyst Enthusiast from Indonesia 🇮🇩</h3>

---

### About Me:

- 🌱 I’m currently learning **Python, JavaScript, PHP**
- 👯 I’m looking to collaborate on **Advanced SQL Queries for Data Warehousing** and **Time Series Forecasting with Python** (or a specific data analysis project that excites you!).
- 💬 Ask me about **Data Visualization, Machine Learning in Python, Data Cleaning Techniques**
- 📫 How to reach me: **suryaputradzaky@gmail.com**

---

<h3 align="left">Connect with me:</h3>
<p align="left">
<a href="https://instagram.com/@whoskyy" target="blank"><img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/instagram.svg" alt="@whoskyy" height="30" width="40" /></a>
</p>

---

<h3 align="left">Languages and Tools I use:</h3>
<p align="left">
    <a href="https://www.mysql.com/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/mysql/mysql-original-wordmark.svg" alt="mysql" width="40" height="40"/> </a>
    <a href="https://opencv.org/" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/opencv/opencv-icon.svg" alt="opencv" width="40" height="40"/> </a>
    <a href="https://pandas.pydata.org/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/2ae2a900d2f041da66e950e4d48052658d850630/icons/pandas/pandas-original.svg" alt="pandas" width="40" height="40"/> </a>
    <a href="https://www.postgresql.org" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/postgresql/postgresql-original-wordmark.svg" alt="postgresql" width="40" height="40"/> </a>
    <a href="https://www.python.org" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg" alt="python" width="40" height="40"/> </a>
    <a href="https://pytorch.org/" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/pytorch/pytorch-icon.svg" alt="pytorch" width="40" height="40"/> </a>
    <a href="https://scikit-learn.org/" target="_blank" rel="noreferrer"> <img src="https://upload.wikimedia.org/wikipedia/commons/0/05/Scikit_learn_logo_small.svg" alt="scikit_learn" width="40" height="40"/> </a>
    <a href="https://seaborn.pydata.org/" target="_blank" rel="noreferrer"> <img src="https://seaborn.pydata.org/_images/logo-mark-lightbg.svg" alt="seaborn" width="40" height="40"/> </a>
    <a href="https://www.tensorflow.org" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/tensorflow/tensorflow-icon.svg" alt="tensorflow" width="40" height="40"/> </a>
</p>

---

# 🌍 Clean Air, Healthy Lives: Analyzing Global Air Quality and Respiratory Health Outcomes

## A Comprehensive Data Analysis Project

Hello there! I'm an enthusiastic Data Analyst, and this project is my endeavor to understand the crucial relationship between air quality and respiratory health on a global scale. With data, we can gain clearer insights into how our environment impacts our lives.

In this repository, I will share my data analysis journey, from data cleaning and in-depth exploration to interactive visualizations that tell a compelling story.

---

### 💡 Why This Project Matters

Air pollution is a global issue affecting millions of people daily. By analyzing air quality data (PM2.5, NO2, PM10) and its impact on hospital admissions, we can:

* **Identify Trends:** Observe how air quality changes over time.
* **Understand Correlations:** Discover relationships between air pollutants and respiratory health problems.
* **Raise Awareness:** Provide data-backed insights for environmental advocacy and public health policies.

---

### 🛠️ Tools and Libraries Used

* **Programming Language:** Python
* **Data Manipulation & Analysis:** `pandas`, `numpy`
* **Static Data Visualization:** `matplotlib`, `seaborn`
* **Interactive Data Visualization:** `plotly`
* **Development Environment:** Google Colab

---

### 📊 Data Analysis Process

#### 1. Data Acquisition

The data is sourced from the "Global Air Quality and Respiratory Health Outcomes" dataset via Kaggle. This process involves Kaggle API authentication and downloading the zipped dataset.

```python
# Library installation
!pip install kaggle

# Upload your kaggle.json
from google.colab import files
files.upload()

# Kaggle API configuration
!mkdir -p ~/.kaggle
!mv kaggle.json ~/.kaggle/
!chmod 600 ~/.kaggle/kaggle.json

# Download dataset
kaggle_dataset_slug = 'tfisthis/global-air-quality-and-respiratory-health-outcomes'
!kaggle datasets download {kaggle_dataset_slug}
