 Importing necessary libraries
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Loading the dataset
filename = "starbucks.csv"
starbucks_data = pd.read_csv(filename)

# EDA Plot 1: Bar plot of Beverage category counts
plt.figure(figsize=(10, 6))
sns.barplot(y=starbucks_data['Beverage_category'].value_counts().index, x=starbucks_data['Beverage_category'].value_counts(), palette='muted')
plt.title('Count of Beverage Categories', fontsize=16)
plt.xlabel('Count', fontsize=14)
plt.ylabel('Beverage Category', fontsize=14)
plt.xticks(fontsize=12)
plt.yticks(fontsize=12)
plt.grid(axis='x', linestyle='--', alpha=0.7)
plt.show()
"""
Insight 1:
The bar plot shows the distribution of beverage categories in the dataset, indicating which categories have the highest number of entries.
"""

# EDA Plot 2: Line plot of Calories by Beverage
plt.figure(figsize=(12, 8))
sns.lineplot(data=starbucks_data, x='Beverage', y='Calories', color='skyblue')
plt.title('Calories by Beverage', fontsize=16)
plt.xlabel('Beverage', fontsize=14)
plt.ylabel('Calories', fontsize=14)
plt.xticks(rotation=90, fontsize=12)
plt.yticks(fontsize=12)
plt.grid(axis='y', linestyle='--', alpha=0.7)
plt.show()
"""
Insight 2:
The line plot displays the variation of calorie content across different beverages, allowing for easy comparison.
"""

# EDA Plot 3: Relationship between Total Fat and Calories
plt.figure(figsize=(12, 8))
sns.scatterplot(data=starbucks_data, x=' Total Fat (g)', y='Calories', color='green')
plt.title('Relationship between Total Fat and Calories', fontsize=16)
plt.xlabel('Total Fat (g)', fontsize=14)
plt.ylabel('Calories', fontsize=14)
plt.xticks(fontsize=12)
plt.yticks(fontsize=12)
plt.grid(linestyle='--', alpha=0.7)
plt.show()
"""
Insight 3:
There seems to be a positive correlation between total fat content and calorie count, which is expected as fat is calorie-dense.
"""

# EDA Plot 4: Boxplot of Sodium content by Beverage category
plt.figure(figsize=(14, 10))
sns.boxplot(data=starbucks_data, x='Beverage_category', y=' Sodium (mg)', palette='pastel')
plt.title('Sodium Content by Beverage Category', fontsize=18)
plt.xlabel('Beverage Category', fontsize=16)
plt.ylabel('Sodium (mg)', fontsize=16)
plt.xticks(rotation=45, fontsize=14)
plt.yticks(fontsize=14)
plt.grid(axis='y', linestyle='--', alpha=0.7)
plt.show()
"""
Insight 4:
Different beverage categories vary significantly in their sodium content, with some outliers indicating particularly high sodium content in certain categories.
"""

# EDA Plot 5: Pairplot for numerical variables (excluding ' Dietary Fibre (g)')

plt.figure(figsize=(14, 10))
sns.pairplot(starbucks_data[['Calories', ' Total Fat (g)', ' Sodium (mg)', ' Dietary Fibre (g)']])
plt.suptitle('Pairplot for Numerical Variables', fontsize=20)
plt.show()
"""
Insight 5:
This pairplot matrix allows us to visualize relationships between various numerical variables. For example, we can observe correlations between Calories and Total Fat, Calories and Sodium, etc.
"""

# EDA Plot 6: Bar plot of Beverage category counts (alternative method)
plt.figure(figsize=(12, 8))
sns.countplot(data=starbucks_data, y='Beverage_category', palette='muted')
plt.title('Count of Beverage Categories', fontsize=16)
plt.xlabel('Count', fontsize=14)
plt.ylabel('Beverage Category', fontsize=14)
plt.xticks(fontsize=12)
plt.yticks(fontsize=12)
plt.grid(axis='x', linestyle='--', alpha=0.7)
plt.show()
"""
Insight 6:
The countplot provides another visualization of the distribution of beverage categories, confirming the findings from the earlier bar plot.
"""

# EDA Plot 7: Correlation Heatmap
plt.figure(figsize=(12, 8))
sns.heatmap(starbucks_data.corr(), annot=True, cmap='coolwarm', linewidths=0.5)
plt.title('Correlation Heatmap of Starbucks Nutrition Variables', fontsize=18)
plt.xticks(fontsize=12)
plt.yticks(fontsize=12)
plt.show()
