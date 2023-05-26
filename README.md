# Ex-08-Data-Visualization-

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
DEVLOPED BY : M.A.Vishal
Reg no: 212222230177
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
df=pd.read_csv("/content/Superstore (2).csv",encoding="ISO-8859-1")
df
df.info()
df.describe()
```
```
sns.lineplot(x="Segment",y="Sales",data=df,marker='o')
plt.title("Segment vs Sales")
plt.xticks(rotation = 90)
plt.show()

sns.barplot(x="Segment",y="Sales",data=df)
plt.xticks(rotation = 90)
plt.show()
```
```
df.shape
df1 = df[(df.Profit >= 60)]
df1.shape

plt.figure(figsize=(30,8))
states=df1.loc[:,["City","Profit"]]
states=states.groupby(by=["City"]).sum().sort_values(by="Profit")
sns.barplot(x=states.index,y="Profit",data=states)
plt.xticks(rotation = 90)
plt.xlabel=("City")
plt.ylabel=("Profit")
plt.show()
sns.barplot(x="Ship Mode",y="Profit",data=df)
plt.show()
sns.lineplot(x="Ship Mode",y="Profit",data=df)
plt.show()
```
```
states=df.loc[:,["Region","Sales"]]
states=states.groupby(by=["Region"]).sum().sort_values(by="Sales")
sns.barplot(x=states.index,y="Sales",data=states)
plt.xticks(rotation = 90)
plt.xlabel=("Region")
plt.ylabel=("Sales")
plt.show()
df.groupby(['Region']).sum().plot(kind='pie', y='Sales',figsize=(6,9),pctdistance=1.7,labeldistance=1.2)
df["Sales"].corr(df["Profit"])
df_corr = df.copy()
df_corr = df_corr[["Sales","Profit"]]
df_corr.corr()
sns.pairplot(df_corr, kind="scatter")
plt.show()
```
```grouped_data = df.groupby('Segment')[['Sales', 'Profit']].mean()
# Create a bar chart of the grouped data
fig, ax = plt.subplots()
ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')
ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')
ax.set_xlabel('Segment')
ax.set_ylabel('Value')
ax.legend()
plt.show()
```
```grouped_data = df.groupby('State')[['Sales', 'Profit']].mean()
# Create a bar chart of the grouped data
fig, ax = plt.subplots()
ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')
ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')
ax.set_xlabel('State')
ax.set_ylabel('Value')
ax.legend()
plt.show()
```
```
grouped_data = df.groupby(['Segment', 'Ship Mode'])[['Sales', 'Profit']].mean()
pivot_data = grouped_data.reset_index().pivot(index='Segment', columns='Ship Mode', values=['Sales', 'Profit'])
# Create a bar chart of the grouped data
fig, ax = plt.subplots()
pivot_data.plot(kind='bar', ax=ax)
ax.set_xlabel('Segment')
ax.set_ylabel('Value')
plt.legend(title='Ship Mode')
plt.show()
```
```
grouped_data = df.groupby(['Segment', 'Ship Mode','Region'])[['Sales', 'Profit']].mean()
pivot_data = grouped_data.reset_index().pivot(index=['Segment', 'Ship Mode'], columns='Region', values=['Sales', 'Profit'])
sns.set_style("whitegrid")
sns.set_palette("Set1")
pivot_data.plot(kind='bar', stacked=True, figsize=(10, 5))
plt.xlabel('Segment-Ship Mode')
plt.ylabel('Value')
plt.legend(title='Region')
plt.show()
```
# OUPUT

![Screenshot 2023-05-15 102804](https://github.com/Dharshan011/Ex-08-Data-Visualization-/assets/113497491/7c3a3622-cb9e-437d-896e-79efa313a060)

![Screenshot 2023-05-15 102820](https://github.com/Dharshan011/Ex-08-Data-Visualization-/assets/113497491/54ef1f21-eabd-40c6-a0e8-2068724af253)


![Screenshot 2023-05-15 102838](https://github.com/Dharshan011/Ex-08-Data-Visualization-/assets/113497491/01245883-f5b0-43a8-871d-f421174af8ff)


![Screenshot 2023-05-15 102854](https://github.com/Dharshan011/Ex-08-Data-Visualization-/assets/113497491/5410df8f-6112-4c03-92a3-b0539d7dbfc8)

![Screenshot 2023-05-15 102904](https://github.com/Dharshan011/Ex-08-Data-Visualization-/assets/113497491/30d7a1e0-5a2d-4201-880f-8ae7f47de151)

![Screenshot 2023-05-15 102917](https://github.com/Dharshan011/Ex-08-Data-Visualization-/assets/113497491/3d03797b-1b66-4517-a1bd-54f6374b8256)

![Screenshot 2023-05-15 102926](https://github.com/Dharshan011/Ex-08-Data-Visualization-/assets/113497491/4e4722b3-8146-437f-ade0-4dbe7ca6b093)

![Screenshot 2023-05-15 102937](https://github.com/Dharshan011/Ex-08-Data-Visualization-/assets/113497491/2cd4471b-b40f-4eda-9090-9832b6c1da28)

![Screenshot 2023-05-15 102944](https://github.com/Dharshan011/Ex-08-Data-Visualization-/assets/113497491/2ddeabc8-4a01-4f22-9171-3169a938d460)

![Screenshot 2023-05-15 102951](https://github.com/Dharshan011/Ex-08-Data-Visualization-/assets/113497491/eaa540e6-16ac-4fe0-aa5f-f2ca08b85b67)

![Screenshot 2023-05-15 102957](https://github.com/Dharshan011/Ex-08-Data-Visualization-/assets/113497491/c795e6d2-d2a0-4ef5-975b-a216a903ede1)

![Screenshot 2023-05-15 103004](https://github.com/Dharshan011/Ex-08-Data-Visualization-/assets/113497491/283c3f51-3e16-4b36-bf2e-b0566f6ad0f7)

![Screenshot 2023-05-15 103011](https://github.com/Dharshan011/Ex-08-Data-Visualization-/assets/113497491/a1d822cc-36ef-43df-94aa-167f4a09a5b3)

![Screenshot 2023-05-15 103023](https://github.com/Dharshan011/Ex-08-Data-Visualization-/assets/113497491/916c50fa-43ff-4d2b-b21a-0e45bb088491)

## RESULT
Hence,Data Visualization is applied on the complex dataset using libraries like Seaborn and Matplotlib successfully and the data is saved to file.


