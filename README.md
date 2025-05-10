# Step 1: Upload the CSV file (only needed for Google Colab)
from google.colab import files
uploaded = files.upload()

# Step 2: Import required libraries
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Step 3: Load the uploaded CSV file
df = pd.read_csv('accidents_2019.csv')  # Make sure the filename matches what you upload

# Step 4: Display basic info
print("First 5 rows of the dataset:")
print(df.head())

print("\nSummary of the dataset:")
print(df.describe(include='all'))

# Step 5: Check for missing values
print("\nMissing values:")
print(df.isnull().sum())

# Step 6: Bar plot of total accidents by State/UT
plt.figure(figsize=(12, 8))
sns.barplot(data=df, x='Total - Total number of Accidents', y='States/UTs', palette='magma')
plt.title('Total Number of Accidents by State/UT')
plt.xlabel('Number of Accidents')
plt.ylabel('States/UTs')
plt.tight_layout()
plt.show()

# Step 7: Correlation heatmap (for numerical columns)
plt.figure(figsize=(14, 10))
numeric_df = df.select_dtypes(include='number')
sns.heatmap(numeric_df.corr(), annot=True, fmt=".2f", cmap='coolwarm')
plt.title('Correlation Heatmap of Accident Data')
plt.show()
