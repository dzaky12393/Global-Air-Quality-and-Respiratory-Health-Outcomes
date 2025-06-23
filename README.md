<h1 align="center">Hi 👋, I'm Dzaky</h1>
<h3 align="center">A passionate Data Analyst Enthusiast from Indonesia</h3>

- 🌱 I’m currently learning **Python, JavaScript, PHP**

- 👯 I’m looking to collaborate on **A specific data analysis project or skill you're trying to master, e.g., "Advanced SQL Queries for Data Warehousing", "Time Series Forecasting with Python**

- 💬 Ask me about **Data Visualization, Machine Learning in Python, Data Cleaning Techniques**

- 📫 How to reach me **suryaputradzaky@gmail.com**

<h3 align="left">Connect with me:</h3>
<p align="left">
<a href="https://instagram.com/@whoskyy" target="blank"><img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/instagram.svg" alt="@whoskyy" height="30" width="40" /></a>
</p>

<h3 align="left">Languages and Tools:</h3>
<p align="left"> <a href="https://www.mysql.com/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/mysql/mysql-original-wordmark.svg" alt="mysql" width="40" height="40"/> </a> <a href="https://opencv.org/" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/opencv/opencv-icon.svg" alt="opencv" width="40" height="40"/> </a> <a href="https://pandas.pydata.org/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/2ae2a900d2f041da66e950e4d48052658d850630/icons/pandas/pandas-original.svg" alt="pandas" width="40" height="40"/> </a> <a href="https://www.postgresql.org" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/postgresql/postgresql-original-wordmark.svg" alt="postgresql" width="40" height="40"/> </a> <a href="https://www.python.org" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg" alt="python" width="40" height="40"/> </a> <a href="https://pytorch.org/" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/pytorch/pytorch-icon.svg" alt="pytorch" width="40" height="40"/> </a> <a href="https://scikit-learn.org/" target="_blank" rel="noreferrer"> <img src="https://upload.wikimedia.org/wikipedia/commons/0/05/Scikit_learn_logo_small.svg" alt="scikit_learn" width="40" height="40"/> </a> <a href="https://seaborn.pydata.org/" target="_blank" rel="noreferrer"> <img src="https://seaborn.pydata.org/_images/logo-mark-lightbg.svg" alt="seaborn" width="40" height="40"/> </a> <a href="https://www.tensorflow.org" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/tensorflow/tensorflow-icon.svg" alt="tensorflow" width="40" height="40"/> </a> </p>


🌍 Clean Air, Healthy Lives: Analyzing Global Air Quality and Respiratory Health Outcomes
A Comprehensive Data Analysis Project
Hello there! I'm an enthusiastic Data Analyst, and this project is my endeavor to understand the crucial relationship between air quality and respiratory health on a global scale. With data, we can gain clearer insights into how our environment impacts our lives.

In this repository, I will share my data analysis journey, from data cleaning and in-depth exploration to interactive visualizations that tell a compelling story.

💡 Why This Project Matters
Air pollution is a global issue affecting millions of people daily. By analyzing air quality data (PM2.5, NO2, PM10) and its impact on hospital admissions, we can:

Identify Trends: Observe how air quality changes over time.
Understand Correlations: Discover relationships between air pollutants and respiratory health problems.
Raise Awareness: Provide data-backed insights for environmental advocacy and public health policies.
🛠️ Tools and Libraries Used
Programming Language: Python
Data Manipulation & Analysis: pandas, numpy
Static Data Visualization: matplotlib, seaborn
Interactive Data Visualization: plotly
Development Environment: Google Colab
📊 Data Analysis Process
1. Data Acquisition
The data is sourced from the "Global Air Quality and Respiratory Health Outcomes" dataset via Kaggle. This process involves Kaggle API authentication and downloading the zipped dataset.

Python

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
2. Data Cleaning & Pre-processing
After the dataset is extracted, the next step is to ensure the data is ready for analysis. This includes:

Loading Data: Loading the CSV file into a Pandas DataFrame.
Data Type Conversion: Converting the 'date' column to datetime type and setting it as the index.
Date Filtering: Filtering data only for the years 2020 to 2025 to focus on recent trends.
Missing Values Handling: Filling missing values (NaN) with the median for numerical columns and the mode for categorical columns.
Duplicate Handling: Dropping duplicate rows to ensure data integrity.
<!-- end list -->

Python

# Example data cleaning code
df['date'] = pd.to_datetime(df['date'])
df.set_index('date', inplace=True)
df_filtered = df[df.index.year <= 2025].copy()

# Handling Missing Values and Duplicates
# ... (full code is in the notebook)
3. Exploratory Data Analysis (EDA)
Distribution of Key Variables
Understanding the distribution of key variables like PM2.5, NO2, PM10, and Hospital Admissions is the first step. This helps us see patterns and the spread of the data.

Python

# Code for distribution plots
plt.figure(figsize=(15, 10))
sns.histplot(df_filtered['pm2_5'], kde=True)
plt.title('Distribusi PM2.5')
# ... (full code is in the notebook)
plt.show()
Correlation Heatmap
A correlation heatmap helps us identify relationships between numerical variables. Is there a strong correlation between air pollutants and hospital admissions?

Python

# Code for correlation heatmap
correlation_matrix = df_filtered.corr(numeric_only=True)
plt.figure(figsize=(14, 10))
sns.heatmap(correlation_matrix, annot=True, cmap='coolwarm', fmt=".2f", linewidths=.5)
plt.title('Heatmap Korelasi Antar Variabel')
plt.show()
Bivariate Relationships
Scatter plots directly show the relationship between PM2.5 and Hospital Admissions. Box plots illustrate the variation in Hospital Admissions across different cities.

Python

# Code for scatter plot and box plot
plt.figure(figsize=(10, 7))
sns.scatterplot(x='pm2_5', y='hospital_admissions', data=df_filtered, alpha=0.6)
plt.title('Hubungan PM2.5 dan Hospital Admissions')
# ... (full code is in the notebook)
plt.show()
4. Monthly Trend Analysis
To understand temporal dynamics, data is aggregated on a monthly basis. This allows us to observe trends in air quality and their impact on respiratory health over time.

Python

# Resampling data to monthly
numeric_cols_for_resampling = [
    'aqi', 'pm2_5', 'pm10', 'no2', 'o3',
    'temperature', 'humidity', 'hospital_admissions', 'hospital_capacity'
]
df_monthly = df_filtered[numeric_cols_for_resampling].resample('ME').mean()

# ... (full code is in the notebook for plotting global trends)
Monthly Average Trends for PM2.5 and Hospital Admissions (2020-2025)
(You can embed an image of the plot here if GitHub allows, or provide a link to the image)

5. Interactive Visualization per City (Plotly)
This is the most exciting part! I created an interactive visualization using Plotly that allows you to select a city and view the monthly trends for PM2.5 and Hospital Admissions specifically for that city. This provides flexibility for in-depth and personalized data exploration.

Python

# Code for Plotly interactive visualization
# ... (full code is in the notebook)
fig_interactive.show()
Click the Buttons Below to See Trends per City:
(Embed the interactive Plotly plot here if GitHub supports Plotly rendering. Otherwise, you can include a GIF or screenshot and direct users to run the notebook in their Colab for the full interactive experience.)

🚀 Conclusion and Next Steps
From this analysis, we can observe patterns and correlations between air quality and respiratory health. Interactive visualizations enable further exploration to uncover city-specific insights.

Possible Next Steps:

Seasonal Analysis: Studying how seasons influence air quality and health cases.
Predictive Modeling: Building models to forecast pollutant levels or hospital admissions.
Analyzing Other Factors: Incorporating factors like environmental policies, population density, and industry.
🤝 Contributions
Suggestions and contributions are highly welcome! If you have ideas to improve this analysis or find any bugs, feel free to open an issue or pull request.

Thank you for exploring my project! Feel free to reach out if you have any questions or would like to collaborate.
