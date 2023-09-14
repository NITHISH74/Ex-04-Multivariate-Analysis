# Ex-04-Multivariate-Analysis
## AIM:
To perform Multivariate EDA on the given data set.

## EXPLANATION:
Exploratory data analysis is used to understand the messages within a dataset. This technique involves many iterative processes to ensure that the cleaned data is further sorted to better understand the useful meaning.The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.

## ALGORITHM:
### STEP 1:
Import the built libraries required to perform EDA and outlier removal.

### STEP 2:
Read the given csv file

### STEP 3:
Convert the file into a dataframe and get information of the data.

### STEP 4:
Return the objects containing counts of unique values using (value_counts()).

### STEP 5:
Plot the counts in the form of Histogram or Bar Graph.

### STEP 6
Use seaborn the bar graph comparison of data can be viewed.

### STEP 7
Find the pairwise correlation of all columns in the dataframe.corr()

### STEP 8
Save the final data set into the file

## PROGRAM:
```python
        import pandas as pd
        import numpy as np
        import matplotlib.pyplot as plt
        import seaborn as sns
        dt=pd.read_csv("/content/titanic_dataset.csv")
        dt
        dt.info()
        dt.set_index("PassengerId",inplace=True)
        dt
        dt.describe()
        dt.nunique()
        dt["Survived"].value_counts()
        per=(dt["Survived"].value_counts()/dt.shape[0]*100).round(2)
        per
        sns.countplot(data=dt,x="Survived")
        fig, ax1=plt.subplots(figsize=(5,5))
        graph=sns.countplot(ax=ax1,x='Survived',data=dt)
        graph.set_xticklabels(graph.get_xticklabels(),rotation=90)
        for p in graph.patches:
          height=p.get_height()
          graph.text(p.get_x()+p.get_width()/2.,height+0.1,height,ha="center")
        dt
        dt.Pclass.unique()
        dt.rename(columns={'Sex':'Gender'},inplace = True)
        dt
        sns.catplot(x="Gender",col='Survived',kind='count',data=dt,height=5, aspect=.7)
        sns.catplot(x="Survived",hue='Gender',kind='count',data=dt)
        fig, ax1=plt.subplots(figsize=(8,5))
        graph = sns.countplot(ax=ax1,data=dt,x='Survived',hue="Pclass",palette="rainbow")
        graph.set_xticklabels(graph.get_xticklabels())
        for p in graph.patches:
          height=p.get_height()
          graph.text(p.get_x()+p.get_width()/2,height+20.8,height,ha="left")
        
        dt.boxplot(column="Age",by="Survived")
        sns.scatterplot(x=dt["Age"],y = dt["Fare"])
        sns.jointplot(x="Age",y ="Fare",data=dt)
        fig, ax1=plt.subplots(figsize=(8,5))
        plot = sns.boxplot(ax=ax1,x='Pclass',y='Age',hue='Gender',data=dt)
        sns.catplot(data=dt,col="Survived",x="Gender",hue="Pclass",kind="count")
        g = sns.catplot(data=dt,col="Survived",x="Gender",hue="Pclass",kind"count",legend=True)
        g.fig.set_size_inches(8,5)
        g.fig.subplots_adjust(top=0.81,right=0.86)
        ax=g.facet_axis(0,0)
        for p in ax.patches:
          ax.text(p.get_x()-0.01,p.get_height()*1.02,'{0:.1f}'.
          format(p.get_height()),color='red',rotation='horizontal',size='small')
        corr=dt.corr()
        sns.heatmap(corr,annot=True)
        sns.pairplot(dt)
```

## OUTPUT:

## RESULT:
