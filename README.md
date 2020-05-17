# Heroes of Pymoli Game - Analysis 

## Purpose

The purpose of this project was to understand the basic user data of the game Heroes of Pymoli. The game data was provided by UC Berkeley extension to further master and practice analysis using Pandas. 

## Objective 
 
The analysis was peformed to understand the quantative data and indicate any trends that can be used by the marketing team to segment and target a user group. 

## Approach
1. Data Cleaning
    - Check for empty columns 
    - Drop the empty columns 
    - Check for value under each column and clean the data if needed
    - Rename Columns for better understanding

2. Perform Analysis 
    * Take each topic and perform quantative analysis. 
    * Put it into a summary table for display

3. Draw Conclusions 
    * Based on the analysis, summarize the conclusions. 

## Conclusions 
* Of the 573 active players, the vast majority are male (82%). There also exists, a smaller, but notable proportion of female players (17%).

* Our peak age demographic falls between 20-24 (45%) with secondary groups falling between 15-19 (17%) and 25-29 (15%).

* Our games have siginificant amount in-app purchases and we can tell the most profitable item was the `ShadowSteel Sword`. 

## Advantages 
* Based on the conclusions above, the marketing team can start to focus on the right users and features to reach the right audience. 
* The advertising can be focused on females and the age groups where the is room for growth. 
* This data can be used to target any stages of the marketing funnel `(Awareness, Acquisition, Activation, Retention, Referral, Revenue).`

## Report 
`PDF/HTML can be found in the 'Reports' Folder.`

**Below is the markdown version:**
### Importing Modules


```python
import pandas as pd
import os
```

### Reading in Data Files 


```python
#path to the data file
file_url = os.path.join('Data','purchase_data_1.json')

#reading the json file into as a DataFrame
user_data_df = pd.read_json(file_url)
```

### Display DataFrame


```python
user_data_df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Age</th>
      <th>Gender</th>
      <th>Item ID</th>
      <th>Item Name</th>
      <th>Price</th>
      <th>SN</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>38</td>
      <td>Male</td>
      <td>165</td>
      <td>Bone Crushing Silver Skewer</td>
      <td>3.37</td>
      <td>Aelalis34</td>
    </tr>
    <tr>
      <th>1</th>
      <td>21</td>
      <td>Male</td>
      <td>119</td>
      <td>Stormbringer, Dark Blade of Ending Misery</td>
      <td>2.32</td>
      <td>Eolo46</td>
    </tr>
    <tr>
      <th>2</th>
      <td>34</td>
      <td>Male</td>
      <td>174</td>
      <td>Primitive Blade</td>
      <td>2.46</td>
      <td>Assastnya25</td>
    </tr>
    <tr>
      <th>3</th>
      <td>21</td>
      <td>Male</td>
      <td>92</td>
      <td>Final Critic</td>
      <td>1.36</td>
      <td>Pheusrical25</td>
    </tr>
    <tr>
      <th>4</th>
      <td>23</td>
      <td>Male</td>
      <td>63</td>
      <td>Stormfury Mace</td>
      <td>1.27</td>
      <td>Aela59</td>
    </tr>
  </tbody>
</table>
</div>



## Data Cleaning 

### Check if all columns are equal: Pass


```python
user_data_df.count()
```




    Age          780
    Gender       780
    Item ID      780
    Item Name    780
    Price        780
    SN           780
    dtype: int64



### Drop empty rows and check the column count again


```python
user_data_df = user_data_df.dropna(how='any')

user_data_df.count()
```




    Age          780
    Gender       780
    Item ID      780
    Item Name    780
    Price        780
    SN           780
    dtype: int64



### Change the column name


```python
user_data_df = user_data_df.rename(columns={'SN':"Username"})
```

### Display the DataFrame after Data Cleaning


```python
user_data_df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Age</th>
      <th>Gender</th>
      <th>Item ID</th>
      <th>Item Name</th>
      <th>Price</th>
      <th>Username</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>38</td>
      <td>Male</td>
      <td>165</td>
      <td>Bone Crushing Silver Skewer</td>
      <td>3.37</td>
      <td>Aelalis34</td>
    </tr>
    <tr>
      <th>1</th>
      <td>21</td>
      <td>Male</td>
      <td>119</td>
      <td>Stormbringer, Dark Blade of Ending Misery</td>
      <td>2.32</td>
      <td>Eolo46</td>
    </tr>
    <tr>
      <th>2</th>
      <td>34</td>
      <td>Male</td>
      <td>174</td>
      <td>Primitive Blade</td>
      <td>2.46</td>
      <td>Assastnya25</td>
    </tr>
    <tr>
      <th>3</th>
      <td>21</td>
      <td>Male</td>
      <td>92</td>
      <td>Final Critic</td>
      <td>1.36</td>
      <td>Pheusrical25</td>
    </tr>
    <tr>
      <th>4</th>
      <td>23</td>
      <td>Male</td>
      <td>63</td>
      <td>Stormfury Mace</td>
      <td>1.27</td>
      <td>Aela59</td>
    </tr>
  </tbody>
</table>
</div>



## Analysis

* Player Count
* Purchasing Analysis (Total)
* Gender Demographics
* Purchasing Analysis (Gender)
* Age Demographics
* Top Spenders
* Most Popular Items
* Most Profitable Items



### Player Count


```python
player_count = len(user_data_df['Username'].unique())
print("Number of Players: {}".format(player_count))
```

    Number of Players: 573


### Purchasing Analysis
* Number of Unique Items
* Average Purchase Price
* Total Number of Purchases
* Total Revenue


```python
unique_items = len(user_data_df['Item ID'].unique())
avg_price = user_data_df['Price'].mean()
total_no_of_purchases = user_data_df['Price'].count()
total_revenue = user_data_df['Price'].sum()

purchasing_analysis_df = pd.DataFrame({
    "Number of Unique Items": unique_items,
    "Average Purchase Price": avg_price,
    "Total Number of Purchases": total_no_of_purchases,
    "Total Revenue": total_revenue,
},index = [0])

# data mugging 
purchasing_analysis_df['Average Purchase Price'] = purchasing_analysis_df['Average Purchase Price'].map("$ {:,.2f}".format)
purchasing_analysis_df['Total Revenue'] = purchasing_analysis_df['Total Revenue'].map("$ {:,.2f}".format)

purchasing_analysis_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Number of Unique Items</th>
      <th>Average Purchase Price</th>
      <th>Total Number of Purchases</th>
      <th>Total Revenue</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>183</td>
      <td>$ 2.93</td>
      <td>780</td>
      <td>$ 2,286.33</td>
    </tr>
  </tbody>
</table>
</div>



### Gender Demographics
* Percentage and Count of Male Players
* Percentage and Count of Female Players
* Percentage and Count of Other / Non-Disclosed


```python
player_demographics = user_data_df[['Gender','Age','Username']]
player_demographics = player_demographics.drop_duplicates()

total_count = player_demographics['Gender'].value_counts()
percentage = round(total_count/player_count * 100,2)

gender_demographics_df = pd.DataFrame({
    "Total Count": total_count,
    "Total Percentage": percentage
})

gender_demographics_df['Total Percentage'] = gender_demographics_df['Total Percentage'].map("{:,.2f}%".format)

gender_demographics_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Total Count</th>
      <th>Total Percentage</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Male</th>
      <td>465</td>
      <td>81.15%</td>
    </tr>
    <tr>
      <th>Female</th>
      <td>100</td>
      <td>17.45%</td>
    </tr>
    <tr>
      <th>Other / Non-Disclosed</th>
      <td>8</td>
      <td>1.40%</td>
    </tr>
  </tbody>
</table>
</div>



### Purchasing Analysis (Gender)

`The below each broken by gender`
* Purchase Count
* Average Purchase Price
* Total Purchase Value
* Normalized Totals


```python
purchase_count = user_data_df.groupby('Gender').count()['Price']
avg_purchase_price = user_data_df.groupby('Gender').mean()['Price']
total_purchase_value = user_data_df.groupby('Gender').sum()['Price']
normalized_total = user_data_df.groupby('Gender').sum()['Price'] / gender_demographics_df['Total Count']

pa = pd.DataFrame({
    "Purchase Count": purchase_count,
    "Average Purchase Price": avg_purchase_price,
    "Total Purchase Value": total_purchase_value,
    "Normalized Totals": normalized_total
})

pa['Average Purchase Price'] = pa['Average Purchase Price'].map("$ {:,.2f}".format)
pa["Total Purchase Value"] = pa["Total Purchase Value"].map("$ {:,.2f}".format)
pa["Normalized Totals"] = pa["Normalized Totals"].map("$ {:,.2f}".format)

pa
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Purchase Count</th>
      <th>Average Purchase Price</th>
      <th>Total Purchase Value</th>
      <th>Normalized Totals</th>
    </tr>
    <tr>
      <th>Gender</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Female</th>
      <td>136</td>
      <td>$ 2.82</td>
      <td>$ 382.91</td>
      <td>$ 3.83</td>
    </tr>
    <tr>
      <th>Male</th>
      <td>633</td>
      <td>$ 2.95</td>
      <td>$ 1,867.68</td>
      <td>$ 4.02</td>
    </tr>
    <tr>
      <th>Other / Non-Disclosed</th>
      <td>11</td>
      <td>$ 3.25</td>
      <td>$ 35.74</td>
      <td>$ 4.47</td>
    </tr>
  </tbody>
</table>
</div>



### Age Demographics
* Percentage and Count by each age range


```python
labels = ['<10','10-14','15-19','20-24','25-29','30-34','35-39','40+']
bins = [0,10,15,20,25,30,35,40,100]

binned = pd.cut(player_demographics['Age'],bins=bins,labels=labels,right=False)
player_demographics['Age Range'] = binned

total_count = player_demographics['Age Range'].value_counts()
percentage = round(total_count/player_count * 100,2)

ad = pd.DataFrame({
    "Total Count": total_count,
    "Total Percentage": percentage
})

ad['Total Percentage'] = ad['Total Percentage'].map("{:,.2f}%".format)

ad
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Total Count</th>
      <th>Total Percentage</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>20-24</th>
      <td>259</td>
      <td>45.20%</td>
    </tr>
    <tr>
      <th>15-19</th>
      <td>100</td>
      <td>17.45%</td>
    </tr>
    <tr>
      <th>25-29</th>
      <td>87</td>
      <td>15.18%</td>
    </tr>
    <tr>
      <th>30-34</th>
      <td>47</td>
      <td>8.20%</td>
    </tr>
    <tr>
      <th>35-39</th>
      <td>27</td>
      <td>4.71%</td>
    </tr>
    <tr>
      <th>10-14</th>
      <td>23</td>
      <td>4.01%</td>
    </tr>
    <tr>
      <th>&lt;10</th>
      <td>19</td>
      <td>3.32%</td>
    </tr>
    <tr>
      <th>40+</th>
      <td>11</td>
      <td>1.92%</td>
    </tr>
  </tbody>
</table>
</div>



### Age Demographics

`The below each broken into bins of 4 years (i.e. <10, 10-14, 15-19, etc.)`
* Purchase Count
* Average Purchase Price
* Total Purchase Value
* Normalized Totals


```python
labels = ['<10','10-14','15-19','20-24','25-29','30-34','35-39','40+']
bins = [0,10,15,20,25,30,35,40,100]

binned = pd.cut(user_data_df['Age'],bins=bins,labels=labels,right=False)
user_data_df['Age Range'] = binned

purchase_count = user_data_df.groupby('Age Range').count()['Price']
avg_purchase_price = user_data_df.groupby('Age Range').mean()['Price']
total_purchase_value = user_data_df.groupby('Age Range').sum()['Price']
normalized_totals = total_purchase_value /ad['Total Count']

age_demographics_df = pd.DataFrame({
    "Purchase Count": purchase_count,
    "Average Purchase Price": avg_purchase_price,
    "Total Purchase Value": total_purchase_value,
    "Normalized Total":normalized_totals
})

age_demographics_df["Average Purchase Price"] = age_demographics_df["Average Purchase Price"].map("$ {:,.2f}".format)
age_demographics_df["Total Purchase Value"] = age_demographics_df["Total Purchase Value"].map("$ {:,.2f}".format)
age_demographics_df['Normalized Total'] = age_demographics_df['Normalized Total'].map("$ {:,.2f}".format)
age_demographics_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Purchase Count</th>
      <th>Average Purchase Price</th>
      <th>Total Purchase Value</th>
      <th>Normalized Total</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>10-14</th>
      <td>35</td>
      <td>$ 2.77</td>
      <td>$ 96.95</td>
      <td>$ 4.22</td>
    </tr>
    <tr>
      <th>15-19</th>
      <td>133</td>
      <td>$ 2.91</td>
      <td>$ 386.42</td>
      <td>$ 3.86</td>
    </tr>
    <tr>
      <th>20-24</th>
      <td>336</td>
      <td>$ 2.91</td>
      <td>$ 978.77</td>
      <td>$ 3.78</td>
    </tr>
    <tr>
      <th>25-29</th>
      <td>125</td>
      <td>$ 2.96</td>
      <td>$ 370.33</td>
      <td>$ 4.26</td>
    </tr>
    <tr>
      <th>30-34</th>
      <td>64</td>
      <td>$ 3.08</td>
      <td>$ 197.25</td>
      <td>$ 4.20</td>
    </tr>
    <tr>
      <th>35-39</th>
      <td>42</td>
      <td>$ 2.84</td>
      <td>$ 119.40</td>
      <td>$ 4.42</td>
    </tr>
    <tr>
      <th>40+</th>
      <td>17</td>
      <td>$ 3.16</td>
      <td>$ 53.75</td>
      <td>$ 4.89</td>
    </tr>
    <tr>
      <th>&lt;10</th>
      <td>28</td>
      <td>$ 2.98</td>
      <td>$ 83.46</td>
      <td>$ 4.39</td>
    </tr>
  </tbody>
</table>
</div>



### Top Spenders
`Identify the the top 5 spenders in the game by total purchase value, then list (in a table):`
* Username
* Purchase Count
* Average Purchase Price
* Total Purchase Value


```python
purchase_count_tp = user_data_df.groupby('Username').count()['Price']
avg_purchase_price_tp = user_data_df.groupby('Username').mean()['Price']
total_purchase_value_tp = user_data_df.groupby('Username').sum()['Price']

top_spender_df = pd.DataFrame({
    "Purchase Count": purchase_count_tp,
    "Average Purchase Price": avg_purchase_price_tp,
    "Total Purchase Value":total_purchase_value_tp
})

top_spender_df['Average Purchase Price'] = top_spender_df['Average Purchase Price'].map("$ {:,.2f}".format)
top_spender_df['Total Purchase Value'] = top_spender_df['Total Purchase Value'].map("$ {:,.2f}".format)

top_spender_df = top_spender_df.sort_values(['Total Purchase Value'],ascending=False)
top_spender_df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Purchase Count</th>
      <th>Average Purchase Price</th>
      <th>Total Purchase Value</th>
    </tr>
    <tr>
      <th>Username</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Qarwen67</th>
      <td>4</td>
      <td>$ 2.49</td>
      <td>$ 9.97</td>
    </tr>
    <tr>
      <th>Sondim43</th>
      <td>3</td>
      <td>$ 3.13</td>
      <td>$ 9.38</td>
    </tr>
    <tr>
      <th>Tillyrin30</th>
      <td>3</td>
      <td>$ 3.06</td>
      <td>$ 9.19</td>
    </tr>
    <tr>
      <th>Lisistaya47</th>
      <td>3</td>
      <td>$ 3.06</td>
      <td>$ 9.19</td>
    </tr>
    <tr>
      <th>Tyisriphos58</th>
      <td>2</td>
      <td>$ 4.59</td>
      <td>$ 9.18</td>
    </tr>
  </tbody>
</table>
</div>



### Most Popular Items

`Identify the 5 most popular items by purchase count, then list (in a table):`
* Item ID
* Item Name
* Purchase Count
* Item Price
* Total Purchase Value


```python
item_data = user_data_df[['Item ID','Item Name','Price']]

purchase_count= item_data.groupby(['Item ID','Item Name']).count()['Price']
avg_purchase_price = item_data.groupby(['Item ID','Item Name']).mean()['Price']
total_purchase_value = item_data.groupby(['Item ID','Item Name']).sum()['Price']

top_item_df = pd.DataFrame({
    "Purchase Count": purchase_count,
    "Average Purchase Price": avg_purchase_price,
    "Total Purchase Value":total_purchase_value
})

top_item_df['Average Purchase Price'] = top_item_df['Average Purchase Price'].map("$ {:,.2f}".format)
top_item_df['Total Purchase Value'] = top_item_df['Total Purchase Value'].map("$ {:,.2f}".format)

top_item_df = top_item_df.sort_values(['Purchase Count'],ascending=False)
top_item_df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>Purchase Count</th>
      <th>Average Purchase Price</th>
      <th>Total Purchase Value</th>
    </tr>
    <tr>
      <th>Item ID</th>
      <th>Item Name</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>39</th>
      <th>Betrayal, Whisper of Grieving Widows</th>
      <td>11</td>
      <td>$ 2.35</td>
      <td>$ 25.85</td>
    </tr>
    <tr>
      <th>84</th>
      <th>Arcane Gem</th>
      <td>11</td>
      <td>$ 2.23</td>
      <td>$ 24.53</td>
    </tr>
    <tr>
      <th>31</th>
      <th>Trickster</th>
      <td>9</td>
      <td>$ 2.07</td>
      <td>$ 18.63</td>
    </tr>
    <tr>
      <th>175</th>
      <th>Woeful Adamantite Claymore</th>
      <td>9</td>
      <td>$ 1.24</td>
      <td>$ 11.16</td>
    </tr>
    <tr>
      <th>13</th>
      <th>Serenity</th>
      <td>9</td>
      <td>$ 1.49</td>
      <td>$ 13.41</td>
    </tr>
  </tbody>
</table>
</div>



### Most Profitable Items

`Identify the 5 most profitable items by total purchase value, then list (in a table):`
- Item ID
- Item Name
- Purchase Count
- Item Price
- Total Purchase Value


```python
top_item_df = top_item_df.sort_values(['Total Purchase Value'],ascending=False)
top_item_df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>Purchase Count</th>
      <th>Average Purchase Price</th>
      <th>Total Purchase Value</th>
    </tr>
    <tr>
      <th>Item ID</th>
      <th>Item Name</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>170</th>
      <th>Shadowsteel</th>
      <td>5</td>
      <td>$ 1.98</td>
      <td>$ 9.90</td>
    </tr>
    <tr>
      <th>21</th>
      <th>Souleater</th>
      <td>3</td>
      <td>$ 3.27</td>
      <td>$ 9.81</td>
    </tr>
    <tr>
      <th>37</th>
      <th>Shadow Strike, Glory of Ending Hope</th>
      <td>5</td>
      <td>$ 1.93</td>
      <td>$ 9.65</td>
    </tr>
    <tr>
      <th>127</th>
      <th>Heartseeker, Reaver of Souls</th>
      <td>3</td>
      <td>$ 3.21</td>
      <td>$ 9.63</td>
    </tr>
    <tr>
      <th>120</th>
      <th>Agatha</th>
      <td>5</td>
      <td>$ 1.91</td>
      <td>$ 9.55</td>
    </tr>
  </tbody>
</table>
</div>


