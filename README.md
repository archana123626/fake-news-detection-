# fake-news-detection-
This project focuses on analyzing and visualizing fake vs real news data using Python. It includes exploratory data analysis (EDA) and multiple visualizations to understand patterns in news categories, sources, and trends over time.
import pandas as pd
import matplotlib.pyplot as plt

# Load dataset
df = pd.read_csv('/content/fake_news_dataset.csv')

# Convert date column to datetime
df['date'] = pd.to_datetime(df['date'], errors='coerce')

# Filter current month (March)
df_month = df[df['date'].dt.month == 3]

# -------------------------------
# 1. Fake vs Real News Count
# -------------------------------
plt.figure()
df_month['label'].value_counts().plot(kind='bar')
plt.title('Fake vs Real News (This Month)')
plt.xlabel('Label')
plt.ylabel('Count')
plt.show()

# -------------------------------
# 2. Top Categories
# -------------------------------
plt.figure()
df_month['category'].value_counts().head(10).plot(kind='bar')
plt.title('Top Categories (This Month)')
plt.xlabel('Category')
plt.ylabel('Count')
plt.show()

# -------------------------------
# 3. Top News Sources
# -------------------------------
plt.figure()
df_month['source'].value_counts().head(10).plot(kind='bar')
plt.title('Top Sources (This Month)')
plt.xlabel('Source')
plt.ylabel('Count')
plt.show()

# -------------------------------
# 4. Daily Trend Analysis
# -------------------------------
plt.figure()
df_month.groupby(df_month['date'].dt.date).size().plot()
plt.title('Daily News Trend (This Month)')
plt.xlabel('Date')
plt.ylabel('Number of Articles')
plt.show()
# Convert date column
df['date'] = pd.to_datetime(df['date'], errors='coerce')

# Filter current month (March)
df_month = df[df['date'].dt.month == 3]

# Pie Chart
plt.figure()
df_month['label'].value_counts().plot(
    kind='pie',
    autopct='%1.1f%%'
)

plt.title('Fake vs Real News Distribution (This Month)')
plt.ylabel('')  # Remove default ylabel
plt.show()
