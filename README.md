# Ex-04-Multivariate-Analysis
# AIM:
To perform Multivariate EDA on the given data set.

# EXPLANATION:
Exploratory data analysis is used to understand the messages within a dataset. This technique involves many iterative processes to ensure that the cleaned data is further sorted to better understand the useful meaning.The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.

# ALGORITHM:
Step1:Import the built libraries required to perform EDA and outlier removal.

Step2:Read the given csv file.

Step3:Convert the file into a dataframe and get information of the data.

Step4:Return the objects containing counts of unique values using (value_counts()).

Step5:Plot the counts in the form of Histogram or Bar Graph.

Step6:Use seaborn the bar graph comparison of data can be viewed.

Step7:Find the pairwise correlation of all columns in the dataframe.corr()

Step8:Save the final data set into the file.

# PROGRAM:
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

dt = pd.read_csv('/content/titanic_dataset.csv')

dt

dt.info()

dt.set_index("PassengerId",inplace=True)

dt.shape

dt.describe()

dt.nunique()

dt["Survived"].value_counts()

per = (dt["Survived"].value_counts()/dt.shape[0]*100).round(2)

per

sns.countplot(data=dt,x="Survived")

dt

dt.Pclass.unique()

dt.rename(columns = {'Sex':'Gender'}, inplace = True)
dt

sns.catplot(x="Gender",col="Survived",kind="count",data=dt,height=5, aspect=.7)

sns.catplot(x='Survived',hue = "Gender",data = dt,kind = "count")

fig, ax1 = plt.subplots(figsize=(8,5))
graph = sns.countplot(ax=ax1,data=dt,x="Survived",hue="Pclass",palette="rainbow")
graph.set_xticklabels(graph.get_xticklabels())
for p in graph.patches:
  height = p.get_height()
  graph.text(p.get_x()+p.get_width()/2, height + 20.8,height,ha="left")

dt.boxplot(column="Age",by="Survived")

sns.scatterplot(x = dt["Age"],y = dt["Fare"])

fig, ax1 = plt.subplots(figsize = (8,5))
pt = sns.boxplot(ax = ax1,x = 'Pclass',y = 'Age', hue='Gender',data=dt)

sns.catplot(data=dt,col="Survived",x="Gender",hue ="Pclass",kind = "count")

g = sns.catplot(data=dt,col="Survived",x="Gender",hue ="Pclass",kind = "count",legend=True)
g.fig.set_size_inches(8,5)
g.fig.subplots_adjust(top=0.81,right=0.86)
ax = g.facet_axis(0,0)
for p in ax.patches:
  ax.text(p.get_x()- 0.01,p.get_height() * 1.02,'{0:.1f}'.format(p.get_height()),color='red',rotation='horizontal',size='small')

## Co-relation
corr = dt.corr()
sns.heatmap(corr,annot=True)

sns.pairplot(dt)
```
# OUTPUT:
![image](https://github.com/vishnupriya20052004/DataScience_4/assets/133640291/936e3146-8e3f-4876-9391-ffeab4cfaa4b)


![image](https://github.com/vishnupriya20052004/DataScience_4/assets/133640291/eeac4eb9-2b7e-47fd-82e0-256c9492cf37)


![image](https://github.com/vishnupriya20052004/DataScience_4/assets/133640291/31d44b1b-cb35-4755-bf45-d06564c12d9e)


![image](https://github.com/vishnupriya20052004/DataScience_4/assets/133640291/11f05f8b-ca95-4843-9ef4-3e48381450e9)


![image](https://github.com/vishnupriya20052004/DataScience_4/assets/133640291/187f3237-2f35-4ff7-8b43-830a3697f7ae)


![image](https://github.com/vishnupriya20052004/DataScience_4/assets/133640291/18295445-387d-449f-b690-6a04e36f15dd)


![image](https://github.com/vishnupriya20052004/DataScience_4/assets/133640291/9a85c326-6468-4fe9-9070-2ad2b96ac4f0)


![image](https://github.com/vishnupriya20052004/DataScience_4/assets/133640291/11a38234-3e68-43d3-8d5e-95819e8da288)


![image](https://github.com/vishnupriya20052004/DataScience_4/assets/133640291/c0db9c85-b472-4f22-8a86-73538a14c24e)


![image](https://github.com/vishnupriya20052004/DataScience_4/assets/133640291/138b8278-63da-48fb-9e2d-a4376b19f57e)


![image](https://github.com/vishnupriya20052004/DataScience_4/assets/133640291/d6761f6d-519b-4d4c-89eb-2371dec812ca)


![image](https://github.com/vishnupriya20052004/DataScience_4/assets/133640291/338e0c82-1bc4-4247-8a81-06d31a2c1883)


![image](https://github.com/vishnupriya20052004/DataScience_4/assets/133640291/d9b7f97e-d833-4945-b598-5890fca764f1)


![image](https://github.com/vishnupriya20052004/DataScience_4/assets/133640291/a0524707-ff77-432a-9800-f00aaef40b85)


![image](https://github.com/vishnupriya20052004/DataScience_4/assets/133640291/f04ee5b8-e076-4b7d-bb7a-0bc522a803b8)


![image](https://github.com/vishnupriya20052004/DataScience_4/assets/133640291/3c291cae-77d4-4146-b8c2-fb4a58d60ed5)


![image](https://github.com/vishnupriya20052004/DataScience_4/assets/133640291/864d24a3-5e9d-47eb-9fe2-619b413b6ddc)


![image](https://github.com/vishnupriya20052004/DataScience_4/assets/133640291/e355546e-276f-4230-a0e1-8ab3d65b60e7)


![image](https://github.com/vishnupriya20052004/DataScience_4/assets/133640291/1e92e395-45ec-4e55-9c2c-dab1ea88ebcf)


![image](https://github.com/vishnupriya20052004/DataScience_4/assets/133640291/ccf47921-4f13-404d-8844-3b7573014535)

![image](https://github.com/vishnupriya20052004/DataScience_4/assets/133640291/88a4f3f3-b6e0-4c9a-940d-aa90a700837d)



# RESULT:
Thus the program to perform EDA on the given data set is successfully executed.
