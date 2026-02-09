# Task-01: Data Visualization using World Population Dataset

# Step 1: Import libraries
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Step 2: Load dataset
df = pd.read_csv("world_population.csv")

# Step 3: Clean column names
df.columns = df.columns.str.strip()

# Step 4: Display basic info
print(df.head())
print(df.info())
print(df.isnull().sum())

# Step 5: Rename columns (to avoid errors)
df = df.rename(columns={
    "Country/Territory": "Country",
    "2022 Population": "Population"
})

# Step 6: Drop missing population values
df = df.dropna(subset=["Population"])

# =========================
# BAR CHART (Categorical)
# Top 10 Countries by Population
# =========================
top10 = df.sort_values(by="Population", ascending=False).head(10)

plt.figure(figsize=(10,6))
sns.barplot(x="Population", y="Country", data=top10)
plt.title("Top 10 Countries by Population")
plt.xlabel("Population")
plt.ylabel("Country")
plt.show()

# =========================
# HISTOGRAM (Continuous)
# Population Distribution
# =========================
plt.figure(figsize=(10,6))
plt.hist(df["Population"], bins=20, edgecolor="black")
plt.title("Distribution of World Population")
plt.xlabel("Population")
plt.ylabel("Number of Countries")
plt.show()


