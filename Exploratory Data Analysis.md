#EDA 
[[Mengatur tampilan folder]]

Based on this [Article](https://levelup.gitconnected.com/exploratory-data-analysis-the-ultimate-workflow-a82b1d21f747)

# Loading libraries and data

# Check Duplicated Data
#duplicated

```python
data.duplicated(subset=['ID']).sum()
```


# Distribution
```python
continuous_vars =  [  
    'Year_Birth', 'Income', 'Kidhome', 'Teenhome',  
    'Recency', 'MntWines', 'MntFruits', 'MntMeatProducts',  
    'MntFishProducts', 'MntSweetProducts', 'MntGoldProds',  
    'NumDealsPurchases', 'NumWebPurchases', 'NumCatalogPurchases',  
    'NumStorePurchases', 'NumWebVisitsMonth'  
    ]  
fig, axes = plt.subplots(4,4) # create figure and axes  
  
for i, el in enumerate(list(data[continuous_vars].columns.values)):  
  a = data.boxplot(el, ax=axes.flatten()[i], fontsize='large')  
  
fig.set_size_inches(18.5, 14)  
plt.tight_layout()   
  
plt.show()
```

![](https://miro.medium.com/v2/resize:fit:1050/1*3N87Wy-PUf6Jxc6wLPhyTQ.png)

Take the time to look at each boxplot individually, and think of what conclusions do you get from each one. Here are mine:


# Categoricals
```python
categorical_vars =  [  
    'Education', 'Marital_Status', 'AcceptedCmp1',  
    'AcceptedCmp2','AcceptedCmp3', 'AcceptedCmp4',  
    'AcceptedCmp5',  'Complain', 'Response'  
    ]  
  
fig, axes = plt.subplots(3,3) # create figure and axes  
  
for i, el in enumerate(data[categorical_vars]):  
  counts = data[el].value_counts()  
  counts.plot(  
      kind="barh",  
      ax=axes.flatten()[i],  
      fontsize='large',  
      color=color  
      ).set_title(el)        
  
fig.set_size_inches(15, 7)  
plt.tight_layout()   
plt.show()
```

![](https://miro.medium.com/v2/resize:fit:1050/1*tHuDr286GK7eEZvRIOUrWg.png)

My conclusions: