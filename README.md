<h1 align="center">Hi 👋, I'm Dzaky</h1>
<h3 align="center">A passionate Data Analyst Enthusiast from Indonesia 🇮🇩</h3>

---

## 👨‍💻 About Me

- 🌱 I’m currently learning **Python, JavaScript, PHP**
- 👯 I’m looking to collaborate on **Advanced SQL Queries for Data Warehousing** and **Time Series Forecasting with Python**
- 💬 Ask me about **Data Visualization, Machine Learning in Python, Data Cleaning Techniques**
- 📫 Reach me at: **suryaputradzaky@gmail.com**

---

## 🌐 Connect with Me

<p align="left">
  <a href="https://instagram.com/whoskyy" target="_blank">
    <img src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/instagram.svg" alt="Instagram: @whoskyy" height="30" width="40" />
  </a>
</p>

---

## 🧰 Languages and Tools

<p align="left">
  <a href="https://www.mysql.com/" target="_blank" rel="noreferrer"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/mysql/mysql-original-wordmark.svg" alt="MySQL" width="40" height="40"/></a>
  <a href="https://opencv.org/" target="_blank" rel="noreferrer"><img src="https://www.vectorlogo.zone/logos/opencv/opencv-icon.svg" alt="OpenCV" width="40" height="40"/></a>
  <a href="https://pandas.pydata.org/" target="_blank" rel="noreferrer"><img src="https://raw.githubusercontent.com/devicons/devicon/2ae2a900d2f041da66e950e4d48052658d850630/icons/pandas/pandas-original.svg" alt="Pandas" width="40" height="40"/></a>
  <a href="https://www.postgresql.org/" target="_blank" rel="noreferrer"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/postgresql/postgresql-original-wordmark.svg" alt="PostgreSQL" width="40" height="40"/></a>
  <a href="https://www.python.org/" target="_blank" rel="noreferrer"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg" alt="Python" width="40" height="40"/></a>
  <a href="https://pytorch.org/" target="_blank" rel="noreferrer"><img src="https://www.vectorlogo.zone/logos/pytorch/pytorch-icon.svg" alt="PyTorch" width="40" height="40"/></a>
  <a href="https://scikit-learn.org/" target="_blank" rel="noreferrer"><img src="https://upload.wikimedia.org/wikipedia/commons/0/05/Scikit_learn_logo_small.svg" alt="Scikit-Learn" width="40" height="40"/></a>
  <a href="https://seaborn.pydata.org/" target="_blank" rel="noreferrer"><img src="https://seaborn.pydata.org/_images/logo-mark-lightbg.svg" alt="Seaborn" width="40" height="40"/></a>
  <a href="https://www.tensorflow.org/" target="_blank" rel="noreferrer"><img src="https://www.vectorlogo.zone/logos/tensorflow/tensorflow-icon.svg" alt="TensorFlow" width="40" height="40"/></a>
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
````

#### 2\. Data Cleaning & Pre-processing

After the dataset is extracted, the next step is to ensure the data is ready for analysis. This includes:

  * **Loading Data:** Loading the CSV file into a Pandas DataFrame.
  * **Data Type Conversion:** Converting the 'date' column to datetime type and setting it as the index.
  * **Filter Tanggal:** Filtering data only for the years 2020 to 2025 to focus on recent trends.
  * **Missing Values Handling:** Filling missing values (NaN) with the median for numerical columns and the mode for categorical columns.
  * **Duplicate Handling:** Dropping duplicate rows to ensure data integrity.

<!-- end list -->

```python
# Example data cleaning code
df['date'] = pd.to_datetime(df['date'])
df.set_index('date', inplace=True)
df_filtered = df[df.index.year <= 2025].copy()

# Penanganan Missing Values
for col in df_filtered.columns:
    if df_filtered[col].isnull().any():
        if df_filtered[col].dtype in ['int64', 'float64']:
            median_val = df_filtered[col].median()
            df_filtered[col].fillna(median_val, inplace=True)
        elif df_filtered[col].dtype == 'object':
            mode_val = df_filtered[col].mode()[0]
            df_filtered[col].fillna(mode_val, inplace=True)

# Penanganan Duplikat
if df_filtered.duplicated().sum() > 0:
    df_filtered.drop_duplicates(inplace=True)
```

#### 3\. Exploratory Data Analysis (EDA)

##### Distribution of Key Variables

Understanding the distribution of key variables like PM2.5, NO2, PM10, and Hospital Admissions is the first step. This helps us see patterns and the spread of the data.

```python
# Code for distribution plots
import matplotlib.pyplot as plt
import seaborn as sns

print("\nDistribusi Variabel Numerik Kunci:")
plt.figure(figsize=(15, 10))

plt.subplot(2, 2, 1)
sns.histplot(df_filtered['pm2_5'], kde=True)
plt.title('Distribusi PM2.5')
plt.xlabel('PM2.5')
plt.ylabel('Frekuensi')

plt.subplot(2, 2, 2)
sns.histplot(df_filtered['no2'], kde=True)
plt.title('Distribusi NO2')
plt.xlabel('NO2')
plt.ylabel('Frekuensi')

plt.subplot(2, 2, 3)
sns.histplot(df_filtered['pm10'], kde=True)
plt.title('Distribusi PM10')
plt.xlabel('PM10')
plt.ylabel('Frekuensi')

plt.subplot(2, 2, 4)
sns.histplot(df_filtered['hospital_admissions'], kde=True)
plt.title('Distribusi Hospital Admissions')
plt.xlabel('Hospital Admissions')
plt.ylabel('Frekuensi')

plt.tight_layout()
plt.show()
```

##### Correlation Heatmap

A correlation heatmap helps us identify relationships between numerical variables. Is there a strong correlation between air pollutants and hospital admissions?

```python
# Code for correlation heatmap
print("\nHeatmap Korelasi Antar Variabel Numerik:")
correlation_matrix = df_filtered.corr(numeric_only=True)
plt.figure(figsize=(14, 10))
sns.heatmap(correlation_matrix, annot=True, cmap='coolwarm', fmt=".2f", linewidths=.5)
plt.title('Heatmap Korelasi Antar Variabel')
plt.show()
```

##### Bivariate Relationships

Scatter plots directly show the relationship between PM2.5 and Hospital Admissions. Box plots illustrate the variation in Hospital Admissions across different cities.

```python
# Code for scatter plot and box plot
print("\nVisualisasi Hubungan Bivariat Kunci:")
plt.figure(figsize=(10, 7))
sns.scatterplot(x='pm2_5', y='hospital_admissions', data=df_filtered, alpha=0.6)
plt.title('Hubungan PM2.5 dan Hospital Admissions')
plt.xlabel('Konsentrasi PM2.5')
plt.ylabel('Jumlah Penerimaan Rumah Sakit')
plt.grid(True, linestyle='--', alpha=0.7)
plt.show()

plt.figure(figsize=(12, 8))
sns.boxplot(x='city', y='hospital_admissions', data=df_filtered)
plt.title('Distribusi Hospital Admissions per Kota')
plt.xlabel('Kota')
plt.ylabel('Jumlah Penerimaan Rumah Sakit')
plt.xticks(rotation=45, ha='right')
plt.grid(True, linestyle='--', alpha=0.7)
plt.tight_layout()
plt.show()
```

#### 4\. Monthly Trend Analysis

To understand temporal dynamics, data is aggregated on a monthly basis. This allows us to observe trends in air quality and their impact on respiratory health over time.

```python
# Resampling data to monthly
import pandas as pd
import matplotlib.pyplot as plt

numeric_cols_for_resampling = [
    'aqi', 'pm2_5', 'pm10', 'no2', 'o3',
    'temperature', 'humidity', 'hospital_admissions', 'hospital_capacity'
]
df_monthly = df_filtered[numeric_cols_for_resampling].resample('ME').mean()

print("\nData Tren Bulanan Global (5 Baris Pertama):")
print(df_monthly.head())

fig_global_trend, ax1_global_trend = plt.subplots(figsize=(15, 7))

ax1_global_trend.plot(df_monthly.index, df_monthly['pm2_5'], color='tab:blue', marker='o', linestyle='-')
ax1_global_trend.set_xlabel('Tanggal')
ax1_global_trend.set_ylabel('Rata-rata PM2.5', color='tab:blue')
ax1_global_trend.tick_params(axis='y', labelcolor='tab:blue')
ax1_global_trend.grid(True, linestyle='--', alpha=0.7)

ax2_global_trend = ax1_global_trend.twinx()
ax2_global_trend.plot(df_monthly.index, df_monthly['hospital_admissions'], color='tab:orange', marker='o', linestyle='-')
ax2_global_trend.set_ylabel('Rata-rata Hospital Admissions', color='tab:orange')
ax2_global_trend.tick_params(axis='y', labelcolor='tab:orange')

plt.title('Tren Rata-rata PM2.5 dan Hospital Admissions Bulanan (2020-2025)')
plt.xlim(pd.Timestamp('2020-01-01'), pd.Timestamp('2025-12-31'))
fig_global_trend.tight_layout()
plt.show()
```

**Monthly Average Trends for PM2.5 and Hospital Admissions (2020-2025)**
*(You can embed an image of the plot here if GitHub allows, or provide a link to the image)*

#### 5\. Interactive Visualization per City (Plotly)

This is the most exciting part\! I created an interactive visualization using Plotly that allows you to select a city and view the monthly trends for PM2.5 and Hospital Admissions specifically for that city. This provides flexibility for in-depth and personalized data exploration.

```python
# Code for Plotly interactive visualization
import plotly.graph_objects as go
import plotly.express as px

# Siapkan data bulanan untuk setiap kota
df_monthly_per_city = {}
unique_cities = df_filtered['city'].unique()

for city in unique_cities:
    df_city = df_filtered[df_filtered['city'] == city].copy()
    df_monthly_per_city[city] = df_city[['pm2_5', 'hospital_admissions']].resample('ME').mean()

fig_interactive = go.Figure()

current_trace_idx = 0
trace_index_map = {}

for city in unique_cities:
    fig_interactive.add_trace(go.Scatter(
        x=df_monthly_per_city[city].index,
        y=df_monthly_per_city[city]['pm2_5'],
        mode='lines+markers',
        name=f'{city} - PM2.5',
        line=dict(color=px.colors.qualitative.Plotly[current_trace_idx % len(px.colors.qualitative.Plotly)]),
        visible=False
    ))
    trace_index_map[f'{city}_pm2_5'] = current_trace_idx
    current_trace_idx += 1

    fig_interactive.add_trace(go.Scatter(
        x=df_monthly_per_city[city].index,
        y=df_monthly_per_city[city]['hospital_admissions'],
        mode='lines+markers',
        name=f'{city} - Hospital Admissions',
        line=dict(color=px.colors.qualitative.Plotly[current_trace_idx % len(px.colors.qualitative.Plotly)], dash='dot'),
        visible=False,
        yaxis='y2'
    ))
    trace_index_map[f'{city}_hospital_admissions'] = current_trace_idx
    current_trace_idx += 1

buttons = []

all_visible_state = [True] * (len(unique_cities) * 2)
buttons.append(dict(
    label='Tampilkan Semua Kota',
    method='update',
    args=[
        {'visible': all_visible_state},
        {'title': 'Tren Bulanan PM2.5 dan Hospital Admissions (Semua Kota)'}
    ]
))

for i, city in enumerate(unique_cities):
    visible_state_for_city = [False] * (len(unique_cities) * 2)
    visible_state_for_city[trace_index_map[f'{city}_pm2_5']] = True
    visible_state_for_city[trace_index_map[f'{city}_hospital_admissions']] = True

    buttons.append(dict(
        label=city,
        method='update',
        args=[
            {'visible': visible_state_for_city},
            {'title': f'Tren Bulanan PM2.5 dan Hospital Admissions di {city}'}
        ]
    ))

fig_interactive.update_layout(
    title_text='Tren Bulanan Kualitas Udara dan Kesehatan per Kota',
    xaxis_title='Tanggal',
    yaxis=dict(
        title='Rata-rata PM2.5',
        side='left',
        showgrid=True,
        zeroline=True
    ),
    yaxis2=dict(
        title='Rata-rata Hospital Admissions',
        side='right',
        overlaying='y',
        showgrid=False,
        zeroline=False
    ),
    updatemenus=[
        dict(
            type="buttons",
            direction="right",
            x=0.0,
            xanchor="left",
            y=1.3,
            yanchor="top",
            buttons=buttons
        ),
    ],
    hovermode='x unified',
    height=600,
    margin=dict(t=220)
)

fig_interactive.show()
```

**Click the Buttons Below to See Trends per City:**
*(Embed the interactive Plotly plot here if GitHub supports Plotly rendering. Otherwise, you can include a GIF or screenshot and direct users to run the notebook in their Colab for the full interactive experience.)*

-----

### 🚀 Conclusion and Next Steps

From this analysis, we can observe patterns and correlations between air quality and respiratory health. Interactive visualizations enable further exploration to uncover city-specific insights.

**Possible Next Steps:**

  * **Seasonal Analysis:** Studying how seasons influence air quality and health cases.
  * **Predictive Modeling:** Building models to forecast pollutant levels or hospital admissions.
  * **Analyzing Other Factors:** Incorporating factors like environmental policies, population density, and industry.

-----

### 🤝 Contributions

Suggestions and contributions are highly welcome\! If you have ideas to improve this analysis or find any bugs, feel free to open an `issue` or `pull request`.

-----

Thank you for exploring my project\! Feel free to reach out if you have any questions or would like to collaborate.

```
```
