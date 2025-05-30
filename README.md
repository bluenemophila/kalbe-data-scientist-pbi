# **Project Overview**

### **Objective**

The project's goal was to perform a comprehensive analysis of customer purchase behaviors and inventory stocking. From inventory team, the goal was to build a **daily sales prediction model** to estimate how much of each product would be sold on given day to manage daily stock levels. Secondly, from the marketing side, the goal was to work on **customer segmentation**, to help the marketing team create more personalized promotions and targeted sales strategies.

### **Tools and Methodologies**

I employed Python for data manipulation and statistical modeling, while Tableau was used for data visualization and reporting. Before working on the project, I performed SQL Operations to get an understanding of the data.

# **The Approach and Process**

### **Database Data Ingestion**

The initial step was done in DBeaver to get general overview of the data, performing some exploratory data analysis with SQL.

### **Data Preprocessing**

Moving on to tackling the goals, the initial step involved cleaning and preparing the dataset, ensuring quality and consistency for analysis. The preprocessing steps included handling missing value, merging relevant tables, and grouping the data to allow for time series analysis. 

### **Exploratory Data Analysis (EDA)**

Through EDA, I identified key patterns in sales data, such as the recurring pattern of sales increase.

### **Customer Segmentation**

Profiling helped segment customers into distinct groups based on purchasing behavior, enabling targeted marketing campaigns.

```python
# Create K-Means cluster of data and save the inertia to check for best number of cluster

inertia= []
for n in range (1,11):
    model = KMeans(n_clusters=n, init='k-means++', n_init = 10, max_iter=100, tol =0.0001, random_state = 100)
    model.fit(clustering)
    inertia.append(model.inertia_)
 
 # Plot the inertia for different clusters and choose the best cluster number
 
plt.figure(figsize=(10,8))
plt.plot(list(range(1,11)), inertia, color = 'blue', marker='o')
plt.title('Inertia vs Number of Cluster', fontsize = 15)
plt.xlabel('Number of Cluster')
plt.ylabel('Inertia')
plt.xticks(list(range(1,11)))
plt.show()

# visualize the clusters based on criterias

fig, ax = plt.subplots(4,1,figsize=(10,10))

sns.histplot(data=cluster_data,x='RecentPurchase',hue='cluster',palette='Set2',ax=ax[0],kde=True)
ax[0].set_title('Purchase Recency')
sns.histplot(data=cluster_data,x='TransactionID',hue='cluster',palette='Set2',ax=ax[1],kde=True)
ax[1].set_title('Purchase Frequency')
sns.histplot(data=cluster_data,x='TotalAmount',hue='cluster',palette='Set2',ax=ax[2],kde=True)
ax[2].set_title('Monetary')
sns.histplot(data=cluster_data,x='Qty',hue='cluster',palette='Set2',ax=ax[3],kde=True)
ax[3].set_title('Quantity')

plt.tight_layout()
plt.show()
```

# **End Results and Recommendations**

### **Strategic Marketing Recommendations**

The customer segmentation can overall be grouped in 3 groups, active, loyal, and potential customer. Marketing strategies can be proposed tailored to the needs of the customers.
