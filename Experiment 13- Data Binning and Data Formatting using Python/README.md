# Data Binning and Data Formatting using Python
                                                                                   
                  
  ## Experiment Details                                                                        
                  
  | Field | Value |                                                                            
  |-------|-------|
  | **Experiment Title** | Data Binning and Data Formatting using Pandas |                     
  | **Date** | 2026-03-20 |
  | **Programming Language** | Python 3.x |                                                    
  | **Libraries Used** | pandas, numpy |
                                                                                               
  ---             

  ## 1. Objective                                                                              
  
  To understand and implement:                                                                 
  - Data binning (discretization) for continuous variables
  - Creating categorical labels from numerical data                                            
  - Data type conversion and formatting
  - Data sorting and unique value extraction                                                   
                                                                                               
  ---
                                                                                               
  ## 2. Theory                                                                                 
  
  ### 2.1 What is Data Binning?                                                                
                  
  Data binning (or discretization) is the process of converting continuous numerical data into 
  discrete categories (bins). This technique is useful for:
  - Simplifying data analysis                                                                  
  - Reducing noise in data                                                                     
  - Creating meaningful groupings for visualization                                            
  - Preparing data for certain machine learning algorithms                                     
                                                                                               
  ### 2.2 Binning Formula                                                                      
                                                                                               
  ```python                                                                                    
  pd.cut(data, bins=[thresholds], labels=[categories])
                                                                                               
  ┌───────────┬─────────────────────────────┐
  │ Parameter │         Description         │                                                  
  ├───────────┼─────────────────────────────┤                                                  
  │ data      │ The numerical column to bin │
  ├───────────┼─────────────────────────────┤                                                  
  │ bins      │ List of boundary values     │                                                  
  ├───────────┼─────────────────────────────┤                                                  
  │ labels    │ Names for each bin category │                                                  
  └───────────┴─────────────────────────────┘                                                  
                  
  2.3 Key Concepts                                                                             
  
  ┌────────────────┬─────────────────────────────────────────────────────┐                     
  │    Concept     │                     Definition                      │
  ├────────────────┼─────────────────────────────────────────────────────┤
  │ Bins           │ Boundary values that divide data into intervals     │
  ├────────────────┼─────────────────────────────────────────────────────┤
  │ Labels         │ Names assigned to each bin interval                 │                     
  ├────────────────┼─────────────────────────────────────────────────────┤                     
  │ Left-inclusive │ Default: bins include left edge, exclude right edge │                     
  └────────────────┴─────────────────────────────────────────────────────┘                     
                  
  ---                                                                                          
  3. Experiment Sections

  3.1 Product Dataset - Price Binning

  Dataset:                                                                                     
  
  data = {                                                                                     
      'Product': ['Laptop', 'Mobile', 'Tablet', 'Headphones', 'Smartwatch', 'Camera'],         
      'Price': [55000, 20000, 30000, 2000, 8000, 450000],                                      
      'Units_Sold': [25, 60, 35, 80, 50, 15]                                                   
  }                                                                                            
                                                                                               
  Binning Parameters:                                                                          
                  
  ┌───────────┬───────────────────────────┐                                                    
  │ Attribute │          Values           │
  ├───────────┼───────────────────────────┤                                                    
  │ Bins      │ [0, 10000, 30000, 60000]  │
  ├───────────┼───────────────────────────┤                                                    
  │ Labels    │ ['Low', 'Medium', 'High'] │
  └───────────┴───────────────────────────┘                                                    
  
  Code:                                                                                        
                  
  df['Price_Category'] = pd.cut(df['Price'], bins=[0,10000,30000,60000],                       
  labels=['Low','Medium','High'])                                                              
  
  Output Categories:                                                                           
                  
  ┌────────────┬────────┬────────────────────┐
  │  Product   │ Price  │   Price_Category   │
  ├────────────┼────────┼────────────────────┤                                                 
  │ Laptop     │ 55000  │ High               │
  ├────────────┼────────┼────────────────────┤                                                 
  │ Mobile     │ 20000  │ Medium             │                                                 
  ├────────────┼────────┼────────────────────┤                                                 
  │ Tablet     │ 30000  │ Medium             │                                                 
  ├────────────┼────────┼────────────────────┤                                                 
  │ Headphones │ 2000   │ Low                │
  ├────────────┼────────┼────────────────────┤                                                 
  │ Smartwatch │ 8000   │ Low                │
  ├────────────┼────────┼────────────────────┤                                                 
  │ Camera     │ 450000 │ NaN (out of range) │
  └────────────┴────────┴────────────────────┘                                                 
                  
  ---
  3.2 Product Dataset - Sales Binning
                                                                                               
  Binning Parameters:
                                                                                               
  ┌───────────┬─────────────────────────────────────────────┐
  │ Attribute │                   Values                    │                                  
  ├───────────┼─────────────────────────────────────────────┤
  │ Bins      │ [0, 30, 60, 100]                            │
  ├───────────┼─────────────────────────────────────────────┤
  │ Labels    │ ['Low Sales', 'Medium Sales', 'High Sales'] │                                  
  └───────────┴─────────────────────────────────────────────┘                                  
                                                                                               
  Code:                                                                                        
                  
  df['Sales_Category'] = pd.cut(df['Units_Sold'], bins=[0,30,60,100], labels=['Low Sales',
  'Medium Sales', 'High Sales'])                                                               
  
  Category Distribution:                                                                       
                  
  ┌────────────────┬──────────────┐
  │  Sales Range   │   Category   │
  ├────────────────┼──────────────┤                                                            
  │ 0 - 30 units   │ Low Sales    │
  ├────────────────┼──────────────┤                                                            
  │ 30 - 60 units  │ Medium Sales │                                                            
  ├────────────────┼──────────────┤
  │ 60 - 100 units │ High Sales   │                                                            
  └────────────────┴──────────────┘                                                            
  
  ---                                                                                          
  3.3 Food Delivery Dataset - Multi-Column Binning
                                                                                               
  Dataset:
                                                                                               
  data = {        
      'Order_ID': [1, 2, 3, 4, 5, 6, 7, 8],
      'Order_Value': [250, 450, 120, 600, 300, 150, 500, 220],                                 
      'Delivery_Time': [30, 45, 15, 60, 20, 35, 50, 28],                                       
      'Distance_km': [5, 10, 3, 8, 6, 2, 9, 4]                                                 
  }                                                                                            
                                                                                               
  Binning Operations:                                                                          
                  
  ┌───────────────┬────────────────┬─────────────────────────────┬─────────────────────────┐   
  │    Column     │      Bins      │           Labels            │         Purpose         │
  ├───────────────┼────────────────┼─────────────────────────────┼─────────────────────────┤   
  │ Delivery_Time │ [0, 20, 40,    │ ['Short', 'Medium', 'Long'] │ Categorize delivery     │
  │               │ 60]            │                             │ duration                │   
  ├───────────────┼────────────────┼─────────────────────────────┼─────────────────────────┤   
  │ Order_Value   │ [0, 200, 400,  │ ['Affordable', 'Luxe',      │ Categorize order price  │
  │               │ 600]           │ 'Gourmet']                  │                         │   
  ├───────────────┼────────────────┼─────────────────────────────┼─────────────────────────┤
  │ Distance_km   │ [0, 3, 6, 10]  │ ['Close', 'Medium', 'Far']  │ Categorize delivery     │   
  │               │                │                             │ distance                │   
  └───────────────┴────────────────┴─────────────────────────────┴─────────────────────────┘
                                                                                               
  Code:           

  df['Delivery_Category'] = pd.cut(df['Delivery_Time'], bins=[0,20,40,60],
  labels=['Short','Medium','Long'])                                                            
  df['MenuPrice_Category'] = pd.cut(df['Order_Value'], bins=[0,200,400,600],
  labels=['Affordable','Luxe','Gourmet'])                                                      
  df['Distance_Category'] = pd.cut(df['Distance_km'], bins=[0,3,6,10],
  labels=['Close','Medium','Far'])                                                             
                  
  ---                                                                                          
  3.4 Data Formatting
                                                                                               
  Data Type Conversion:
                                                                                               
  df['Units_Sold'] = df['Units_Sold'].astype(float)
  df['Price'] = df['Price'].astype(float)                                                      
  df['Distance_km'] = df['Distance_km'].astype(float)                                          
                                                                                               
  Text Standardization:                                                                        
                                                                                               
  df['Product'] = df['Product'].str.upper()  # Convert to uppercase                            
  df['Price_Category'] = df['Price_Category'].str.upper()
                                                                                               
  Purpose: Ensure consistent data types and text format for analysis.                          
                                                                                               
  ---                                                                                          
  3.5 Data Sorting
                  
  Code:
                                                                                               
  sorted_df = df.sort_values(by='Price')                                                       
  sorted_df = df.sort_values(by='Order_Value')                                                 
                                                                                               
  Sorting Options:

  ┌─────────────────┬──────────────────────────┐
  │    Parameter    │       Description        │
  ├─────────────────┼──────────────────────────┤
  │ by='column'     │ Sort by specified column │
  ├─────────────────┼──────────────────────────┤
  │ ascending=True  │ Default ascending order  │                                               
  ├─────────────────┼──────────────────────────┤
  │ ascending=False │ Sort in descending order │                                               
  └─────────────────┴──────────────────────────┘                                               
  
  ---                                                                                          
  3.6 Unique Values
                                                                                               
  Code:
                                                                                               
  print(df['Price_Category'].unique())
                                                                                               
  Output: Returns array of unique category values in the column.                               
  
  ---                                                                                          
  4. Key Learnings
                                                                                               
  4.1 Binning Best Practices
                                                                                               
  ┌────────────────────────────────────────┬───────────────────────────────────┐
  │                Practice                │              Reason               │               
  ├────────────────────────────────────────┼───────────────────────────────────┤               
  │ Define bins that cover all data points │ Prevents NaN values               │
  ├────────────────────────────────────────┼───────────────────────────────────┤               
  │ Use meaningful labels                  │ Improves readability              │               
  ├────────────────────────────────────────┼───────────────────────────────────┤               
  │ Consider data distribution             │ Choose appropriate bin boundaries │               
  ├────────────────────────────────────────┼───────────────────────────────────┤               
  │ Handle outliers                        │ Values outside bins become NaN    │
  └────────────────────────────────────────┴───────────────────────────────────┘               
                  
  4.2 pd.cut() vs pd.qcut()                                                                    
                  
  ┌───────────┬───────────────────────────────────────┐                                        
  │ Function  │               Use Case                │
  ├───────────┼───────────────────────────────────────┤                                        
  │ pd.cut()  │ Equal-width bins (fixed intervals)    │
  ├───────────┼───────────────────────────────────────┤                                        
  │ pd.qcut() │ Equal-frequency bins (quantile-based) │                                        
  └───────────┴───────────────────────────────────────┘                                        
                                                                                               
  4.3 Common Issues & Solutions                                                                
                  
  ┌───────────────────────────┬───────────────────────────────────────┐                        
  │           Issue           │               Solution                │
  ├───────────────────────────┼───────────────────────────────────────┤
  │ Values become NaN         │ Extend bin range to cover min/max     │
  ├───────────────────────────┼───────────────────────────────────────┤
  │ Wrong category assignment │ Check bin boundaries (left-inclusive) │                        
  ├───────────────────────────┼───────────────────────────────────────┤                        
  │ Data type errors          │ Use astype() before operations        │                        
  └───────────────────────────┴───────────────────────────────────────┘                        
                  
  ---                                                                                          
  5. Workflow Diagram
                                                                                               
  ┌─────────────────────────────────────────────────────────┐
  │                  DATA BINNING WORKFLOW                   │                                 
  ├─────────────────────────────────────────────────────────┤                                  
  │                                                         │                                  
  │   ┌──────────────┐      ┌──────────────┐               │                                   
  │   │ Load Dataset │ ───► │ Define Bins  │               │                                   
  │   └──────────────┘      │ & Labels     │               │                                   
  │                         └──────┬───────┘               │                                   
  │                                │                        │                                  
  │                                ▼                        │                                  
  │                         ┌──────────────┐               │                                   
  │                         │  pd.cut()    │               │                                   
  │                         └──────┬───────┘               │                                   
  │                                │                        │                                  
  │                                ▼                        │
  │                         ┌──────────────┐               │                                   
  │                         │ New Category │               │
  │                         │    Column    │                │
  │                         └──────┬───────┘               │                                   
  │                                │                        │
  │                                ▼                        │                                  
  │                         ┌──────────────┐               │                                   
  │                         │   Format &   │               │                                   
  │                         │   Sort Data  │               │                                   
  │                         └──────────────┘               │                                   
  │                                                         │                                  
  └─────────────────────────────────────────────────────────┘                                  
                                                                                               
  ---                                                                                          
  6. Summary Table

  ┌────────────────┬───────────────┬───────────────────────────────────────────────────────┐
  │   Operation    │   Function    │                        Example                        │
  ├────────────────┼───────────────┼───────────────────────────────────────────────────────┤   
  │ Binning        │ pd.cut()      │ pd.cut(df['Price'], bins=[0,100,200],                 │
  │                │               │ labels=['A','B'])                                     │   
  ├────────────────┼───────────────┼───────────────────────────────────────────────────────┤   
  │ Type           │ astype()      │ df['col'].astype(float)                               │   
  │ Conversion     │               │                                                       │   
  ├────────────────┼───────────────┼───────────────────────────────────────────────────────┤   
  │ Uppercase      │ str.upper()   │ df['col'].str.upper()                                 │
  ├────────────────┼───────────────┼───────────────────────────────────────────────────────┤   
  │ Sorting        │ sort_values() │ df.sort_values(by='Price')                            │
  ├────────────────┼───────────────┼───────────────────────────────────────────────────────┤
  │ Unique Values  │ unique()      │ df['col'].unique()                                    │
  └────────────────┴───────────────┴───────────────────────────────────────────────────────┘   
  
  ---                                                                                          
  7. Conclusion   

  This experiment demonstrated:
  - Creating categorical variables from continuous data using binning
  - Customizing bin boundaries and labels                                                      
  - Applying binning to multiple columns 
  - Formatting and standardizing data types                                                    
  - Sorting and extracting unique values   
                                                                                               
  Data binning is essential for:                                                               
  - Feature engineering in machine learning                                                    
  - Creating meaningful visualizations                                                         
  - Simplifying complex datasets for analysis
                                                                                               
  ---                                                                                          
  8. References                                                                                
                                                                                               
  - Pandas Documentation: https://pandas.pydata.org/docs/
  - pd.cut() Reference: https://pandas.pydata.org/docs/reference/api/pandas.cut.html           
  - Data Discretization:                                                                       
  https://pandas.pydata.org/pandas-docs/stable/user_guide/basics.html#discretization  
