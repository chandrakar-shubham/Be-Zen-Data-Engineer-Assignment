# Be-Zen-Data-Engineer-Assignment

This code can be directly run from google collabnotebook or pycharm or jupyter notebook

Resources:
1. Rar file (which contains csv): https://drive.google.com/file/d/1AVg8ENuzzvmBWhzFRUgT1os7E8IO78Tq/view?usp=sharing
2. CSV file (link after extraction): https://drive.google.com/file/d/1oY3t46RrGi4IzZM4qEtjLR40Tm_hPSv_/view?usp=sharing
3. Google collabnote book to run code: https://colab.research.google.com/drive/1ePJ7c3dh70wiP_PS5G5sciKGVYsLOffT?usp=sharing
   or any other platform can be used to run python code;
   .py file link = https://github.com/chandrakar-shubham/Be-Zen-Data-Engineer-Assignment/blob/main/data_engineer_assignment.py

To extract Rar to location library used:

pip install unrar
pip install rarfile
import rarfile
rar = rarfile.RarFile(path_rar)
rar.extractall(path = path_to_extract)


Implementation of task required for assignment as performed in the following manner:

Technology used = Python(google collab notebook)

1. importing pandas and numpy
2. Extraction of CSV file from Rar and storing it in Gdrive then import it in dataframe
These paths need to be provided so as to suceesfully run the code:

(a) path_rar =  path where rar is stored
(b) path_to_extract =path where to extract rar
(c) path_csv = path which contains extracted csv

After that this "rarfile" library is used to extract csv:

pip install unrar
pip install rarfile
import rarfile
rar = rarfile.RarFile(path_rar)
rar.extractall(path = path_to_extract)


Csv file will now be extracted.

3. Creation of dataframe "df"

4. Data Cleaning after creating DataFrame
(a) removal of duplicated rows and updation of dataframe
(b) removal of null product_type column
(c) Data wrangling is done to undestand data

5. Checking distribution products_type containing null and non null prices in column price_string

6. Checking distribution of level_1 containing null and non null prices in column price_string

7. Checking distribution of category containing null and non null prices in column price_string

8. Checking price_string column
(a) Conversion of column data type to string

9 . EDA on price string with NULL value and comparision with
(a) product type vs null price_sring
(b) category vs null price_sring
(c) level 1 vs null price_sring
with charts and visualisation 


10. Seperating data frame consisting of null prices in price_string columns
(a) creating data frame with null price_string
price_null_df= df[df['price_string'].isnull()]

11. EDA on price string with NULL price_string

(a)Count of Product type having null price in price_string
Distribution Unique product with null price
top 10 product with null price bar plot

(b) Count of category with null price in price_string column
Distribution Unique category with null price
top 10 unique category with null price bar plot

(c) Count of level 1 having null price in price_string column
Distribution of level 1 with null price
top 10 level 1 with null price


11. EDA on data frame with non null prices in prices_string column

(a) creating copy of dataframe df with alias df1
df1 = df.copy()

Note: to avoid any data distortion in original df

(b) Creating seperate dataframe with name "non_null_prices_df" containing non null prices

non_null_prices_df = df1[~df1['price_string'].isnull()]

(c) Correcting Product Prices in the correct format (eg: $56)

custom function used:

def modify_price(x):
  '''add $ sign to Correct Product Prices in the correct format (eg: $56)'''

  if x[0]!='$':
    x1 = "$"+ x
    return x1
  else:
    return x
    
(d)  create currency name column for US dollar column value will be "USD"

non_null_prices_df['currency'] = non_null_prices_df['price_string'].apply(create_currency)

custom function used:
def create_currency(x):
  '''return USD if first element is "$"'''
  if x[0] == '$':
    return 'USD'
  else:
    'Not'
    
(e) create currency value column for price

non_null_prices_df['value'] = non_null_prices_df['price_string'].apply(only_currency_value)

custom function used:

def only_currency_value(x):
  '''converts currency to only value discard symbol such as $23.00 to  23.00'''
  if x[0] == '$':
    return x[1:]
  else:
    'Not'
    
(f) Changing data type of value column to float to do calculation

non_null_prices_df['value']=non_null_prices_df['value'].astype("float")

(f) Distribution of all prices is visualised

(g) Count of products with non null prices in each unique product type

distribution plot of count of product with non null prices
top 10 product type with highest count of non_null prices
Visualisation top 10 product type with highest count bar plot

(h) Avg price of products with prices in each Product Type
distribution plot of avg_price with respect to product type
top 10 product type with highest avg price
Visualisation top 10 product type with highest avg price bar plot

(i) Count of unique category with non null prices
distribution plot of count of non null prices with respect to category
top 10 category_count with highest count of non null prices
Visualisation top 10 category_count with highest count of non null prices

(j) Unique Categories with average price of product
distribution plot of avg_price with respect to category
top 10 category with highest avg price
Visualisation top 10 cateory with highest avg price

(k) Count of level 1 with non null prices
distribution plot of level 1 with respect to count
top 10 level1 count with highest count of non null prices
Visualisation top 10 category_count with highest count of non null prices

(j) Unique level1 with average price of product
distribution plot of avg_price with respect to level_1
top 10 level 1 with highest avg value in level_1
Visualisation top 10 level_1 with highest avg price

12. Final dataframe combined and cleaned is created as "df_optimised"
This dataframe is combination of price_null_df,non_null_prices_df.

data_frames = [price_null_df,non_null_prices_df]
df_optimised = pd.concat(data_frames)

price_null_df : contains all columns with null prices in price_string column
non_null_prices_df : contains all columns with non-null prices in price_string column



This dataframe contains:
1. Prices in correct format
2. dataframe is cleaned of duplicates
3. contains null and non null prices both














