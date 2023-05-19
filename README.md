# Ex-07-Data-Visualization-

## AIM
To Perform Data Visualization on the given dataset and save the data to a file. 

# Explanation
Data visualization is the graphical representation of information and data. By using visual elements like charts, graphs, and maps, data visualization tools provide an accessible way to see and understand trends, outliers, and patterns in data.

# ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Clean the Data Set using Data Cleaning Process
### STEP 3
Apply Feature generation and selection techniques to all the features of the data set
### STEP 4
Apply data visualization techniques to identify the patterns of the data.


# CODE
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sbn
df=pd.read_csv("/content/Superstore(1).csv",encoding='windows-1252')
df.head()

df.info()
df.isnull().sum()
1.Which Segment has Highest sales?
sbn.barplot(x=df['Segment'],y=df['Sales'])
plt.title("Highest Sales of the segment")

2.Which City has Highest profit?
sbn.barplot(x=df['City'],y=df['Profit'])
plt.title("Highest Profit of cities")

City=df.loc[:,["City","Profit"]]
df.head(5)
City=City.groupby(by=["City"]).sum().sort_values(by="Profit")
plt.figure(figsize=(10,10))
sbn.barplot(x=City.index,y="Profit",data=City)
plt.xticks(rotation = 90)
plt.xlabel=("City")
plt.ylabel=("Profit")
plt.show()

3.Which ship mode is profitable?
sbn.barplot(x=df['Ship Mode'],y=df['Profit'])
plt.title("Profitable Ship Mode")

4.Sales of the product based on region.
sbn.barplot(x=df['Sales'], y=df['Region'])
plt.title("Sales of Product based on Region")

5.Find the relation between sales and profit.
sbn.lineplot(x=df['Sales'], y=df['Profit'])
plt.title("Relation between Sales and Profit")

6.Find the relation between sales and profit based on the following category. i) Segment ii)City iii)States iv)Segment and Ship Mode
v)Segment, Ship mode and Region 
i) Segment
grouped_data = df.groupby('Segment')[['Sales', 'Profit']].mean()
# Create a bar chart of the grouped data
fig, ax = plt.subplots()
ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')
ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')
ax.set_xlabel('Segment')
ax.set_ylabel('Value')
ax.legend()
plt.title("Sales and Profit based on Segment")
plt.show()

2.City
grouped_data = df.groupby('City')[['Sales', 'Profit']].mean()
# Create a bar chart of the grouped data
fig, ax = plt.subplots()
ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')
ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')
ax.set_xlabel('City')
ax.set_ylabel('Value')
ax.legend()
plt.title("Sales and Profit based on City")
plt.show()

3.states
grouped_data = df.groupby('State')[['Sales', 'Profit']].mean()
# Create a bar chart of the grouped data
fig, ax = plt.subplots()
ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')
ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')
ax.set_xlabel('State')
ax.set_ylabel('Value')
ax.legend()
plt.title("Sales and Profit based on States")

4.Segment and Ship Mode
grouped_data = df.groupby(['Segment', 'Ship Mode'])[['Sales', 'Profit']].mean()
pivot_data = grouped_data.reset_index().pivot(index='Segment', columns='Ship Mode', values=['Sales', 'Profit'])
# Create a bar chart of the grouped data
fig, ax = plt.subplots()
pivot_data.plot(kind='bar', ax=ax)
ax.set_xlabel('Segment')
ax.set_ylabel('Value')
plt.legend(title='Ship Mode')
plt.legend(loc="best")
plt.title("Sales and Profit based on Segment and Ship mode")
plt.show()

5.Segment, Ship mode and Region
grouped_data = df.groupby(['Segment', 'Ship Mode','Region'])[['Sales', 'Profit']].mean()
pivot_data = grouped_data.reset_index().pivot(index=['Segment', 'Ship Mode'], columns='Region', values=['Sales', 'Profit'])
sbn.set_style("whitegrid")
sbn.set_palette("Set1")
pivot_data.plot(kind='bar', stacked=True, figsize=(8, 5))
plt.legend(title='Region')
plt.legend(loc='best')
plt.title("Sales and Profit based on Segment,Ship mode and Region")
```
# OUPUT

![Screenshot 2023-05-19 103832](https://github.com/sujithrabkn/Ex-08-Data-Visualization-/assets/119477857/130e0735-d17b-4232-97f9-30d8ab8c63e4)

![Screenshot 2023-05-19 103839](https://github.com/sujithrabkn/Ex-08-Data-Visualization-/assets/119477857/a2ef00f8-216b-428f-9830-7b54f8829ce0)

![Screenshot 2023-05-19 103847](https://github.com/sujithrabkn/Ex-08-Data-Visualization-/assets/119477857/c2cecc50-f754-41a8-bec3-759c7dd8b37a)

![Screenshot 2023-05-19 103905](https://github.com/sujithrabkn/Ex-08-Data-Visualization-/assets/119477857/aaf9c7e8-00fc-457e-96a4-e668820c4500)

![Screenshot 2023-05-19 103942](https://github.com/sujithrabkn/Ex-08-Data-Visualization-/assets/119477857/f99a0f80-6457-45fa-8578-b97ebab9743c)

![Screenshot 2023-05-19 104002](https://github.com/sujithrabkn/Ex-08-Data-Visualization-/assets/119477857/9d14223a-aa90-4826-b639-c9d23fd40c1f)

![Screenshot 2023-05-19 104046](https://github.com/sujithrabkn/Ex-08-Data-Visualization-/assets/119477857/92ff84d6-3d33-43b9-9513-2e267ba1f77a)

![Screenshot 2023-05-19 104054](https://github.com/sujithrabkn/Ex-08-Data-Visualization-/assets/119477857/30d41a1b-f64b-410f-90fb-b6d1013dcafa)

![Screenshot 2023-05-19 104108](https://github.com/sujithrabkn/Ex-08-Data-Visualization-/assets/119477857/3792d9ce-8779-40c7-843d-0baa505c71fe)

![Screenshot 2023-05-19 104122](https://github.com/sujithrabkn/Ex-08-Data-Visualization-/assets/119477857/adda5399-eb27-45f7-84f2-89050e08ad27)

![Screenshot 2023-05-19 104134](https://github.com/sujithrabkn/Ex-08-Data-Visualization-/assets/119477857/3cba528a-3e0b-4da7-bfad-0555ef7f6c8c)

![Screenshot 2023-05-19 104144](https://github.com/sujithrabkn/Ex-08-Data-Visualization-/assets/119477857/cbbcf6e2-7c7a-49a0-9d62-cf6fff298c55)

![Screenshot 2023-05-19 104156](https://github.com/sujithrabkn/Ex-08-Data-Visualization-/assets/119477857/556f5663-3a7f-401e-9100-7b1c254add29)

![Screenshot 2023-05-19 104210](https://github.com/sujithrabkn/Ex-08-Data-Visualization-/assets/119477857/ad6f0d38-0911-4e59-9a8f-96c8301c307c)

# Result :
Hence the data visualization method for the given dataset applied successfully.

