# Climate-Change-Analysis-project-code

import ast
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
import numpy as np
# pd.set_option('max_columns', 200)

df = pd.read_csv('C:/Users/gigam/Downloads/climatechangedata.csv')

df.shape

df.head()

df.columns

df.dtypes

df.describe()

df['Date'] = pd.to_datetime(df['Date'])

df['Date'].dt.year

df['year'] = df['Date'].dt.year
df

new_df = df[['year', 'Country', 'City']]
new_df

average_by_country = df.groupby(['year', 'Country', 'City'])['Humidity'].mean()
print(average_by_country)

average_by_country = df.groupby(['year', 'Country', 'City'])['Heat Index'].mean()
print(average_by_country)

average_by_country = df.groupby(['year', 'Country', 'City'])['Wind Speed'].mean()
print(average_by_country)

average_by_country = df.groupby(['year', 'Country', 'City']).agg({
    'Humidity': 'mean',
    'Heat Index': 'mean'
}).reset_index()
print(average_by_country)
