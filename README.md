# Business Case: Real-time Crypto Currency Performance and Sentiment Analysis Report
# Executive Summary
This business case proposes the development of a real-time dashboard that provides comprehensive insights into the performance and sentiment surrounding the top  cryptocurrencies. By leveraging advanced data analytics tools and APIs, this dashboard will empower stakeholders with critical information to make informed decisions in the volatile cryptocurrency market.

## Problem Statement
The cryptocurrency market is characterized by rapid price fluctuations, evolving regulatory landscapes, and diverse investor sentiment. Lack of access to real-time, comprehensive data can lead to suboptimal investment decisions and missed opportunities.

## Proposed Solution
The proposed solution involves the following steps:
- Data Extraction: Utilize the CoinMarketCap API to extract live data on the top cryptocurrencies, including market capitalization, trading volume, price, and 
  other relevant metrics. Also wewill leverage Google Custom Search Engine API to extract latest information, news,opinions and insightson the crypto market.
- Data Transformation: Employ Synapse Data Engineer in Microsoft Fabric to transform and cleanse the extracted data, ensuring data quality and consistency.
- Sentiment Analysis: Leverage the Google CSE JSON API to extract daily news and opinions related to the top  cryptocurrencies. Perform sentiment analysis using 
  Synapse Data Science to gauge market sentiment and identify emerging trends.
- Dashboard Development:Create a Semantic Model(Entity Relation Diagram) for the Crypto Data Table and Crpto News Table In Lakehouse, this serves as the bases of 
  our dynamic report in Power BI which visualizes key performance indicators (KPIs) for each cryptocurrency, including price charts, 
  trading volume trends, and sentiment analysis results.
- Data Activator: To configure  email alerts in Power BI visuals for negative market sentiments shaped by latest news, opinions and releases in the digital asset 
  space.
- Orchestrate the whole process as an End-to-End Pipeline using Microsoft Fabric- Data Factory.

## Benefits
- Real-time Insights: Access up-to-date information on cryptocurrency performance and sentiment.
- Informed Decision-Making: Support investment decisions based on data-driven insights.
- Risk Mitigation: Identify potential risks and opportunities by monitoring market trends.
- Competitive Advantage: Gain a competitive edge by having access to in-depth market intelligence.

## Technical Approach
- Data Sources: CoinMarketCap API, Google CSE JSON API
- Data Ingestion: Data Factory in Microsoft Fabric
- Data Transformation: Synapse Data Engineer in Microsoft Fabric
- Sentiment Analysis: Synapse Data Science in Microsoft Fabric
- Live Crypto Currency Report: Semantic Model & Power BI in Microsoft Fabric

Project Timeline
Phase 1: Data Extraction and Transformation: 2 weeks
Phase 2: Sentiment Analysis: 3 weeks
Phase 3: Dashboard Development: 4 weeks
Cost Estimate
[Provide a detailed cost estimate based on resource requirements, cloud platform costs, and licensing fees.]

Return on Investment (ROI)
[Quantify the potential benefits of the dashboard, such as increased investment returns, reduced risk, and improved decision-making. Calculate the ROI based on the cost estimate and expected benefits.]

# Conclusion
The proposed cryptocurrency performance and sentiment analysis dashboard offers a valuable tool for stakeholders seeking to navigate the complex and dynamic cryptocurrency market. By providing real-time insights and supporting informed decision-making, this dashboard can contribute to significant business value.

## SolutionArchitecture

![Crypto Project Solution Architecture drawio](https://github.com/user-attachments/assets/d9e2ab89-4a48-49a6-8d1e-25cec9956867)

## Tools Used



## Environment setup
##### There are mainly two ways to extract data from a website or webpage. One, using the API of the website . Two, through web scraping by accessing the HTML of the webpage to extract data. In this project we shall be using APIs to extract data from two different sources.
Configuring Your Data Sources

### 1.Create a free CoinMarketCap API 
Steps:
##### API KEY
- Log on to: https://coinmarketcap.com/api/
- On the window, click "GET YOUR API KEY NOW"
- Fill the sign up form, create and verify your account
Then, a CoinMarketCap  "Developers" dashboard appears
- Under API KEY, click "Copy Key"
- Save the copied key in a secure place as your API Key
##### Header
- Then, on the bottom left, click on "API DOCUMENTATION" to find information about available API and their usage
  - On the left, click on "AUTHENTICATION" tab
  - Then, "AUTHENTICATION" --> "Using Your API key"--> "Preferred method" --> header named "X-CMC_PRO_API_KEY" to get your API header
##### Base url
- Then, to your left, click on "CRYPTOCURRENCY" (- From the drop down, you have list of Base URL to extract specific crypto data according to your need, but in this project we are picking a base url that will give us the latest listings price of crypto currencies )
- From the drop down, choose "Quotes Latest v2"
- On your top right, you will see a sample IDE, click on it to copy your Base URL (https://pro-api.coinmarketcap.com/v1/cryptocurrency/listings/latest)
##### Query Parameters
- Below "Listing Latest" documentation, you will find list of query parameters attached to this base url in a tabular form. You can optimize you API query base on this parameters.

### 2.Creating and configuring Google Custom Search Engine
Prerequisite: A Gmail account
Steps:
- Log on to Google Cloud Platform: https://console.cloud.google.com/welcome?project
- On the top-left, Click on "My Google Search API"
- From the dropdown, on the top-right, click "New Project"
- Under "Project Name" to the left, Input your project name <My Google Search API 2>
- Then, click "Create" button.
Then on Google Cloud Window, Under Quick Access
- Click on "API Apis& Service" tab,--> Library-->
- From the appear window, scroll down and choose "Custom Search API"
- Click "Enable"
- To the top-left, click on "Credentials" button.
- At the top, click "+ Create Credentials"
- From the drop-down, click "API Key"
- Copy and save generated API key in a secure place, then  click close button
- Then click on "Enable APIs & Service" to the left.
- Then, click on "Custom Search API" below.
- To your mid-right, under (Explore), click "TRY IN API EXPLORER"
This take you to a new window
- Click on "Get A KEY"
- An "Enable Custom Search API" title appears, click on the drop-down "Select or Create Project"
- Pick the name of the project you created in step 4 above "My Google Search API 2"
- Click NEXT
- Click on "SHOW KEY"
- Copy API Key  to secure place. The same API as the first API
- Click DONE
Back on The Programmable Search Engine
- Click on the highlighted "Control Panel". A new window appears" Create a new search engine"
- Field "Name Your Search Engine" : "Business Insight"
- Field "What to search" : "Search the entire web"
- Field "Search Setting" : Check "Image Search" and "Safe Search"
- To your left, click " Search Features"
  - Under "Query Enhancement"
    - Fill appropriately "Keywords"
    - Fill appropriately "Quert addition"
    - Fill appropriately "Web search extra query terms"
- Click "Create"
Your New Search Engine has been created . Copy the Search Engine ID

Use this Code Snippet as your Google CSE JSON API call
- https://www.googleapis.com/customsearch/v1?key=YOUR_API_KEY&cx=YOUR_SEARCH_ENGINE_ID&q=SEARCH_QUERY&searchType=image
###### Use Google Translate to run the Code Snippet
Where
- Customize Google URL for your CSE = <https://www.googleapis.com/customsearch/v1> 
- Key Or API Key = YOUR_API_KEY
- cx = YOUR_SEARCH_ENGINE_ID
- q = SEARCH_QUERY&searchType=image

### 3a.Create and configure Power BI Workspace for this project
Prerequisite: Enable Microsoft Fabric in Power BI Account as an Admin or Tenant.
- Go to (app.powerbi.com)
- Navigate to "workspaces" tab on the left
- At the bottom, click( + New Workspace )
  - A drop down at the top right; Enter name of workspace " Crypto Project "
  - Optional: In the description box, give detail description of project.
  - Scroll downward to "Advance" assign licensing to the workspace by clicking on "Trial" if you using trial version or " Premium Capacity", if you are using premium license.
  - Click Apply button

### 3b. Create and configure Storage in Fabric environment, i.e. Lakehouse Database.
Switch from Power BI environment to Data Engineering environment
- Click on the Power BI icon on the bottom left.
- Then, click on the "Data Engineering " Component
- Then, click on Lakehouse icon
- From the dropdown, "Name Lakehouse"- <Google_Custom_SearchDB>
- Click "create"

## DATA INGESTION
In the data ingestion stage, we will be creating two different Data Factory to extracting  two separate set of data from different sources using different APIs,  The data are 
1.Daily statistics of to top crypto currencies and 
2. Latest News and opinions on crypto currencies.

#### Data Ingestion For Crypto Data
Using the Data Factory component of Fabric.
- On the bottom left, click on the Power BI icon.
- From the list of icons, click the "Data Factory" icon to move into Data Factory environment
- Click on the "Data Pipeline" tab, to create a new pipeline for the Data Factory.
- Name Pipeline "US Election Data Pipeline "
- Then, click "Create" to create Data Factory Pipeline
- At the top, click on "Copy Data" tab, from the drop-down, choose "Add to Canvas" to copy data from Source(CoinMarketCap) to Destination(Lakehouse Database)
- In Data Factory canvas --> "General" tab --> "Name" : Copy daily crypto statistics.
- Then Click on "Source" tab. To configure Source Connection
  - In "Connection" field, Click on the drop-down and select "more"(because our data source is outside of Fabric Environment)
  - New Sources--> click on "View more"-->Scroll down and select "REST" from variety of options. REST is the resource use for connecting to APIs
  - On "Connection Setting" heading, enter Base URL(https://pro-api.coinmarketcap.com/v1/cryptocurrency/listings/latest?limit=35)
  - On "Connection Credentials" sub-heading, input connection name, say (Crypto_currencies). This is for easy reference purpose.
  - Then, click "Connect"
  - Test Data Factory connection to  API Data Source, by clicking on the " Test Connection" tab. Connection was successful, this prove that Data Factory has establish connection with          CoinMarketCap.
  - On the left, click "Advance"  --> Additional Headers "+" --> input headers name (X-CMC_PRO_API_KEY) and your API Key (***************)
 - Preview Data, by clicking on the "Preview Data" tab
   
##### Screen Shot
![Screenshot 2024-09-15 203757](https://github.com/user-attachments/assets/c5dd4a9a-237f-465a-8162-c5f7639c24d4)

- Click on "Destination" tab
  - On "Connection" field drop-down, select previously created Lakehouse Database "Crypto"
  - On " Root Folder" field, Choose "File".- File because we 're copying the raw data in a JSON format.
  - On "File Path" field, Leave the "Directory" field empty. Fill the "File Name" with a file name, say(crypto_data.json). This will be the file name in the of copy data in destination Lakehouse DB.
  -On "File Format" field drop-down, choose "JSON"
  - Then, click on the "save" tab at the top-left to save the pipeline
  - Click "Run" tab at the top to run pipeline.
Data is Successfully copy from CoinMarketCap End point source to Lakehouse DB

##### Screen Shot
![Screenshot 2024-09-15 204810](https://github.com/user-attachments/assets/2e4c9794-df48-49d4-a699-21c219170e53)

#### Data Ingestion For Crypto News & Opinions
Using the Data Factory component of Fabric.
- On the bottom left, click on the Power BI icon.
- From the list of icons, click the "Data Factory" icon to move into Data Factory environment
- Click on the "Data Pipeline" tab, to create a new pipeline for the Data Factory.
- Name Pipeline,say (Digital Currency)
- Then, click "Create" to create Data Factory Pipeline
- On the Data Factory canvas
- At the top, click on "Copy Data" tab, from the drop-down, choose "Add to Canvas" to copy data from Source(Google CSE JSON API) to Destination(Lakehouse Database)
- In Data Factory canvas --> "General" tab --> "Name" : "Copy latest  Crypto news_opinions"
- Then Click on "Source" tab. To configure Source Connection
  - In "Connection" field, Click on the drop-down and select "more"(because our data source is outside of Fabric Environment)
  - New Sources--> click on "View more"-->Scroll down and select "REST" from variety of options. REST is the resource use for connecting to APIs
  - On "Connection Setting" heading-->Base URL, input Endpoint and Query Parameter(s) ( https://www.googleapis.com/customsearch/v1?q=YOUR_QUERY&cx=YOUR_ENGINE_ID&key=YOUR_API_KEY&q=SEARCH_QUERY)
  - On "Connection Credentials" sub-heading-->, input connection name for ease of reference purpose, say "crypto_new_opinions_CSE"
  - Then, click "Connect"
  - Test Data Factory connection to  API Data Source, by clicking on the " Test Connection" tab. Connection was successful, this prove that  Data Factory has establish connection to my Google CSE JSON API source.
  - Preview Data, by clicking on the "Preview Data" tab
 - ***IMAGE

![Screenshot 2024-09-15 222203](https://github.com/user-attachments/assets/6fe9b7fe-a508-49eb-92df-86229c6dc4b8)

- Click on "Destination" tab
  - On "Connection" field drop-down, select previously created Lakehouse Database "Crypto"
  - On " Root Folder" field, Choose "File".- File because we 're copying the raw data in a JSON format.
  - On "File Path" field, Leave the "Directory" field empty. Fill the "File Name" with a file name, say(crypto-news-opinion.json). This will be the file name in the of copy data in destination Lakehouse DB.
  - On "File Format" field drop-down, choose "JSON"
  - Then, click on the "save" tab at the top-left to save the pipeline
  - Click "Run" tab at the top to run pipeline.
Data is Successfully copy from Google CSE end point to Lakehouse DB

![Screenshot 2024-09-15 221748](https://github.com/user-attachments/assets/589bdf88-db34-4237-b56d-1cb8ab14bd45)



## DATA TRANSFORMAION
In the data transformation phase, we will be processing our data using two different Spark Notebooks to transform extracted data from CoinMarketCap API and Google CSE API respectively.

#### Data Transformation For Crypto Data
This is done using Synapse Data Engineering Component of Fabric.
- On the bottom left, click on the Power BI icon or whatever icon present there.
- From the list of icons, choose Synapse Data Engineering. 
- In Synapse Data Engineering environment, click on "Notebook" tab,-To create a Spark Notebook to "transform" the raw json file into a clean data table.
- On the top-left, click on the Notebook name and rename appropriately for ease referencing.
Step 1.
Use the created Notebook to import and read the raw json file that exist in stored Lakehouse Database.
- On the Left, click on "Lakehouse" button.
- On the left, click "Add Lakehouse" button.- This help in accessing the different tables and files that reside in the Lakehouse Database directly from the Notebook.
- Choose "Existing Lakehouse".
- Click "Add".
- Check or choose the Lakehouse where the raw json data resides.
- Click "Add".
- From the imported Lakehouse Database to the left, click on "File " (-This shows all files that reside in the Lakehouse Database),then "..." , then "Load Data" 
- There are two options (Spark or Pandas), Choose "Spark". 
A code is automatically generated to read the raw json file as a Pyspark DataFrame.

```

df = spark.read.option("multiline", "true").json("Files/crypto_data.json")
# df now is a Spark DataFrame containing JSON data from "Files/crypto_data.json".
display(df)

```

```
# To check Schema, data type of each column and if the data is nested or in array or  not
df.printSchema()

```

```

from pyspark.sql.functions import explode, col

# Explode the 'data' array to get individual records
exploded_df = df.select(explode(col('data')).alias('data'))

```

```
# Define the list of cryptocurrencies to extract from the list of 35 crypto currencies.
cryptos_to_extract = ['Bitcoin', 'Ethereum', 'Tether USDt', 'BNB', 'Solana', 'Dogecoin', 'USDC', 'XRP', 'Toncoin', 'TRON', 'Cardano', 'Avalanche']

# Filter and select the required fields
filtered_df = exploded_df.select(
    col('data.name').alias('Name'),
    col('data.symbol').alias('Symbol'),
    col('data.quote.USD.price').alias('Price'),
    col('data.quote.USD.market_cap').alias('Market Cap'),
    col('data.quote.USD.volume_24h').alias('Volume (24h)'),
    col('data.quote.USD.percent_change_24h').alias('Percent Change (24h)'),
    col('data.circulating_supply').alias('Circulating Supply'),
    col('data.total_supply').alias('Total Supply'),
    col('data.quote.USD.fully_diluted_market_cap').alias('Fully Diluted Market Cap'),
    col('data.last_updated').alias('Last Updated')
).filter(col('Name').isin(*cryptos_to_extract))

# Display the filtered data
filtered_df.show(truncate=False)

```

```
from pyspark.sql.functions import col

# Rename columns in DataFrame to match the Delta table schema to improve code readability, consistency, reliability and robustness
renamed_df = filtered_df.select(
    col('Name').alias('name'),
    col('Symbol').alias('symbol'),
    col('Price').alias('price'),
    col('Market Cap').alias('market_cap'),
    col('Volume (24h)').alias('volume_24h'),
    col('Percent Change (24h)').alias('percent_change_24h'),
    col('Circulating Supply').alias('circulating_supply'),
    col('Total Supply').alias('total_supply'),
    col('Fully Diluted Market Cap').alias('fully_diluted_market_cap'),
    col('Last Updated').alias('last_updated')
)

```

```
display(renamed_df)

```
##### Screen Shot.

![Screenshot 2024-09-17 114244](https://github.com/user-attachments/assets/9fb63932-011c-4f66-ad5f-32bce082c02c)


```
# Write the DataFrame to the Delta table
renamed_df.write.format("delta") \
    .mode("append") \
    .saveAsTable("crypto.tbl_currency_data")

```


#### Data Transformation For Crypto News & Opinions
```
df = spark.read.option("multiline", "true").json("Files/crypto1-news-opinion.json")
# df now is a Spark DataFrame containing JSON data from "Files/crypto1-news-opinion.json".
display(df)
```

```
#Select the items column where the nested data is and ignore the other columns.

df = df.select(["items"])

```

```
from pyspark.sql.functions import explode

# Explode json object(items) as an alias(json_object)

df_exploded = df.select(explode(df["items"]).alias("json_object"))

```

```

display(df_exploded)

```

```

# Converting the Exploded Json Dataframe to a single Json string list,i.e. "json_list" variable

json_list = df_exploded.toJSON().collect()

```

```
#Testing the JSON string,by fetching all the 10 json object and see their json structure

print(json_list)

```

```
# Fectching just one of the json object to view its json structure

print(json_list[0])
```
```
"""
We need to process these JSON structures to extract the desired information 
and create a clean table format. However, since the output is a string, it presents challenges in retrieving the necessary data. 
To extract the information, we would need to write regular expressions and other processing steps because it is a string.
 To simplify this process, we should convert the JSON string into a JSON dictionary, making it much easier to access all or selected information.
 For that, we will be using this function <json.loads>
"""
```
```
# First, we import the json library <import json>, then load a sample news article (json_list[0])
import json

# Convert the JSON String to a JSON dictionary
news_json =json.loads(json_list[0])

```

```
# Our output is a json dictionary, though look similar to a json string.
print(news_json)
```
```
"""
Now we can easily use the json dictionary to process the data and get information out of it.
For example let us get a snippet of the news article [0]
"""
```
```
"""
Testing the JSON Dictionary. In order to get the 'snippet' value from our dictionary news article [0]. 
We needed to see where the snippet property lies within the json dictionary.It lies within the "json_object"
of the dictionary,then we drill in inside 'json-object' to extract the 'snippet' value.
Note, this text output is made possible because the json is a dictionary.
"""

display(news_json["json_object"]["snippet"])

```

```
"""
selecting the information we need in a news article [0], these selected information (link,title,snippet,) 
will be our Column Titles or the Schema of our DataFrame. To extract these information easily from the json dictionary,
let us make use on an online json parser <jason.parser.online> to see the exact detail structure of this json file
"""

print(news_json["json_object"]["link"])
print(news_json["json_object"]["title"])
print(news_json["json_object"]["snippet"])


"""
The above code is just an example to extract information from a news article out of a possible 10 news articles
"""
```

```
"""
 To fetch selected information from the json dictionary, iterating over all the articles. 
 Note, date is not found in the news article, but we fetched the datecolumn from the time stamp 
attached to each snippet found in each news article.
"""
import json
import re
from datetime import datetime, timedelta

link = []
title = []
snippet = []
date = []  # New list for storing the extracted date

# Function to extract date from the "snippet"
def extract_date_from_snippet(snippet_text):
    # Regular expression to capture time (e.g., "6 hours ago", "2 days ago")
    match = re.search(r'(\d+)\s*(hour|day)s?\s*ago', snippet_text)
    
    if match:
        amount = int(match.group(1))  # e.g., "6"
        unit = match.group(2)  # e.g., "hours" or "days"
        
        # Subtract the time from current datetime to get the correct date
        if unit == 'hour':
            date_parsed = datetime.now() - timedelta(hours=amount)
        elif unit == 'day':
            date_parsed = datetime.now() - timedelta(days=amount)
        return date_parsed.date()  # Return only the date part
    else:
        return None  # If no timestamp is found, return None

# Process each JSON object in the list
for json_str in json_list:
    try:
        # Parse the JSON string into a dictionary
        article = json.loads(json_str)

        # Extract information from the dictionary
        link.append(article["json_object"]["link"])
        title.append(article["json_object"]["title"])
        snippet_text = article["json_object"]["snippet"]
        snippet.append(snippet_text)

        # Extract the date from the snippet and append to date list
        extracted_date = extract_date_from_snippet(snippet_text)
        date.append(extracted_date)

    except Exception as e:
        print(f"Error processing JSON object {e}")

```

```
# Print out the results
for l, t, s, d in zip(link, title, snippet, date):
    print(f"Link: {l}, Title: {t}, Snippet: {s}, Date: {d}")

```

```
"""
combining all the list together and create a Dataframe with a defined Schema, so that we can get a proper table structure
to view all the extracted information about the news
"""

from pyspark.sql.types import StructType, StructField, StringType, DateType

# Using the zip function to combine all the list we have created so far and this complete list is stored as a data
data = list(zip(link, title, snippet, date))

# Create a DataFrame from the extracted data . i.e.All individual list will be a column in our DataFrame and these columns are defined bt their data type
schema = StructType([
    StructField("Link", StringType(), True),
    StructField("Title", StringType(), True),
    StructField("Snippet", StringType(), True),
    StructField("Date", DateType(), True)
])

df_cleaned = spark.createDataFrame(data, schema)

```

```
display(df_cleaned)
```
##### Screen Shot

![Screenshot 2024-09-17 193202](https://github.com/user-attachments/assets/a3054099-9b52-44b7-9b3d-09f33f7166a7)

```
from pyspark.sql.functions import col

# Renamed col[link] to url

df_cleaned_final = df_cleaned.withColumnRenamed("link","url")

```

```
display(df_cleaned_final)

```
##### Screen Shot


![Screenshot 2024-09-17 193056](https://github.com/user-attachments/assets/899a8068-8b3c-4b3e-8b5e-649ad21c904d)

#### Handling Incrementa Loading For Crypto News & Opinions

To capture new, updated and unchanged News items and opinions on the US election , we will be employing incremental loading to our dataset using Slowly Changing Dimension Type_1. i.e SCD1. SCD Type1 is a form of incremental load technique in which new records are captured and updated records are overwritten and old records dropped and unchanged records remained unchanged.In SCD1 the table will always hold the present values and not the previous values. It does not keep historical records rather present records. This is good for sentiment analysis, where focus is on present perspectives and not comparison between historical and present perspectives.

```
from pyspark.sql.utils import AnalysisException
from pyspark.sql import functions as F

table_name = "Crypto.news_opinions"

# Check if the table exists
def check_table_exists(spark, table_name):
    try:
        return spark.catalog.tableExists(table_name)
    except AnalysisException:
        return False

try:
    if not check_table_exists(spark, table_name):
        # Save the DataFrame as a new Delta table if it doesn't exist
        df_cleaned_final.write.format("delta").saveAsTable(table_name)
        print(f"Table {table_name} created successfully.")
    else:
        print("Table Already Exists")

        # Preprocess the source DataFrame to remove duplicates
        df_cleaned_dedup = df_cleaned_final.dropDuplicates(subset=["url"])

        # Create or replace a temporary view for the deduplicated DataFrame
        df_cleaned_dedup.createOrReplaceTempView("vw_df_cleaned_final")

        # Perform the MERGE operation
        merge_query = f"""
            MERGE INTO {table_name} target_table
            USING vw_df_cleaned_final source_view

            ON source_view.url = target_table.url

            WHEN MATCHED AND (
                source_view.Title <> target_table.Title OR
                source_view.Snippet <> target_table.Snippet OR
                source_view.Date <> target_table.Date
            )
            THEN UPDATE SET *
            WHEN NOT MATCHED THEN INSERT *
        """
        # Execute the MERGE statement
        spark.sql(merge_query)
        print("Table merged successfully with new data.")

except Exception as e:
    print(f"An error occurred: {str(e)}")

```

### Crypto Data

##### DATA CLEANING (Continuation of Transformation of Crypto Data).
This is done using Synapse Data Engineering Component of Fabric.
- On the bottom left, click on the Power BI icon or whatever icon present there.
- From the list of icons, choose Synapse Data Engineering. 
- In Synapse Data Engineering environment, click on "Notebook" tab,-To create a Spark Notebook to "transform" the raw json file into a clean data table.
- On the top-left, click on the Notebook name and rename appropriately foe ease referencing.
Step 1.
Use the created Notebook to import and read the delta table that exist in stored Lakehouse Database.
- On the Left, click on "Lakehouse" button.
- On the left, click "Add Lakehouse" button.- This help in accessing the different tables and files that reside in the Lakehouse Database directly from the Notebook.
- Choose "Existing Lakehouse".
- Click "Add".
- Check or choose the Lakehouse where the delta table resides.
- Click "Add".
- From the imported Lakehouse Database to the left, click on "Tables " (-This shows all tables that reside in the Lakehouse Database),then "..." , then "Load Data" 
- There is one option (Spark), Choose "Spark".  The code to read the delta table is automatically populated.

```
df = spark.sql("SELECT * FROM Crypto.tbl_currency_data")
display(df)

```
```

# Removing timestamp from the last_updated columnimport pyspark.sql.functions as F

# Assuming your DataFrame is named 'df' and the column containing the timestamp is 'last_updated'
df = df.withColumn(
    "Date",
    F.to_date(F.col("last_updated"))
)

```

```
display(df)

```

```
from pyspark.sql.functions import col, to_date

# Drop the 'last_updated' column, so that we won't have duplicate date columns
df = df.drop("last_updated").drop("symbol")

# Convert the 'Date' column from string to date format
df_crypto_data = df.withColumn("Date", to_date(col("Date"), "yyyy-MM-dd"))


```

```
display(df_crypto_data)

```

```
df_crypto_data.printSchema()

```



```
# Cleaned output of Crypto data
display(df_crypto_data)

```
##### Screen Shot

![Screenshot 2024-09-19 224406](https://github.com/user-attachments/assets/c88cf7ee-adc5-499f-8678-a39d65fb56fb)

```
# Write the DataFrame to the Delta table
df_crypto_data_cleaned.write.format("delta") \
    .mode("append") \
    .saveAsTable("crypto.tbl_cleaned_data")

```

##### SENTIMENT ANALYSIS USING SYNAPSE MACHINE LEARNING(Incremental Loading).
This is done using Synapse Data Science Component of Fabric.
- On the bottom left, click on the Power BI icon or whatever icon present there.
- From the list of icons, choose Synapse Data Science option. 
- In Synapse Data science environment, click on "Notebook" tab,-To use pre-trained Machine Learning Model.
- On the top-left, click on the Notebook name and rename appropriately for ease referencing.
Steps:
Use the created Notebook to import and read the cleaned data stored in a delta table in Lakehouse Database.
- On the Left, click on "Lakehouse" button.
- On the left, click "Add Lakehouse" button.- This help in accessing the different tables and files that reside in the Lakehouse Database directly from the Notebook.
- Choose "Existing Lakehouse".
- Click "Add".
- Check or choose the Lakehouse where the data resides.
- Click "Add".
- From the imported Lakehouse Database to the left, click on "Tables " (-This shows tables that reside in the Lakehouse Database),then "..." , then "Load Data" 
- Then, Choose "Spark".
A code is automatically generated to read the raw delta table as a Pyspark DataFrame.


```

df = spark.sql("SELECT * FROM Crypto.news_opinions ")
display(df)

```

```

# import the synapse ML library (Use a pre-trained intelligent model called AnalyzeText)

import synapse.ml.core
from synapse.ml.services import AnalyzeText

```

```
#Import the Model and configure the Input and Output column
model = (AnalyzeText()
        .setTextCol("Snippet")    # Column we are using to predict the sentiment of the news
        .setKind("SentimentAnalysis") #Select the keywords of ML task, bcos we have a couple of ML task, Such as Language detector, sentiment analysis etc.
        .setOutputCol("response") # Specifying the column name to store the actual output that the ML generates, here we specify the output name as response
        .setErrorCol("error"))  # If something goes wrong while performing the ML task, this column will capture the errorand if everythingworks fine, thiscolumnwe have null value

```

```

#Apply the model to our Dataframe
result = model.transform(df)

```

```

display(result)

```

```

from pyspark.sql.functions import col

sentiment_df = result.withColumn("sentiment", col("response.documents.sentiment"))

```

```

display(sentiment_df)

```
##### Screen Shot


![Screenshot 2024-09-19 025054](https://github.com/user-attachments/assets/f3aceb18-2b10-42dd-9f6a-28a7f38823d5)

```

sentiment_df_final = sentiment_df.drop("error", "response")

```

```

display(sentiment_df_final)

```
##### Screen Shot

![Screenshot 2024-09-19 025423](https://github.com/user-attachments/assets/69192402-f652-4f65-9d72-960d9d8fe8fc)

```

from pyspark.sql.utils import AnalysisException
from pyspark.sql import functions as F

table_name = "Crypto.sentiments"

# Check if the table exists
def check_table_exists(spark, table_name):
    try:
        return spark.catalog.tableExists(table_name)
    except AnalysisException:
        return False

try:
    if not check_table_exists(spark, table_name):
        # Save the DataFrame as a new Delta table if it doesn't exist
        sentiment_df_final.write.format("delta").mode("append").saveAsTable(table_name)
        print(f"Table {table_name} created successfully.")
    else:
        print("Table Already Exists")

        # Preprocess the source DataFrame to remove duplicates
        sentiment_df_dedup = sentiment_df_final.dropDuplicates(subset=["url"])

        # Create or replace a temporary view for the deduplicated DataFrame
        sentiment_df_dedup.createOrReplaceTempView("vw_sentiment_df_final")

        # Perform the MERGE operation
        merge_query = f"""
            MERGE INTO {table_name} target_table
            USING vw_sentiment_df_final source_view

            ON source_view.url = target_table.url

            WHEN MATCHED AND (
                source_view.Title <> target_table.Title OR
                source_view.Snippet <> target_table.Snippet OR
                source_view.Date <> target_table.Date
            )
            THEN UPDATE SET *
            WHEN NOT MATCHED THEN INSERT *
        """
        # Execute the MERGE statement
        spark.sql(merge_query)
        print("Table merged successfully with new data.")

except Exception as e:
    print(f"An error occurred: {str(e)}")

```
## Power BI Report

### Semantic Model
In order to utilize our data in creating  Crypto report in Power BI, we need to create a Semantic Model. Semantic Model is an advance Entity Relation Diagram of Business intelligence which leverage on the relationship between the Crypto Data table and Crypto Sentiment Table. In building the Semantic Model, we will be using the crypto data table and the crypto  sentiments table.

Steps:
- Go to Lakehouse Database
- At the top left, click on "New Semantic Model"
- Under (Direct Lake Semantic Model Name),Give name to your Semantic Model.
- Under "workspace" Choose the appropriate Workspace where the Data Model is to be created
- Scroll down, select the 2 table(s) you want to include the semantic model, i.e. "sentiments" and "table_cleaned_data" tables, then click (Confirm) to create your Semantic Model.

##### Data Model Image


![Screenshot 2024-09-19 221011](https://github.com/user-attachments/assets/a5c2a8b9-489c-4ea1-9e3f-212f3f584d33)


##### Using Semantic Model To Build Power BI Report

Move back to your workspace.
- In your workspace, you will see the drop-down of all the resources you have created in your workspace.
- select the Semantic Model.
- At the top, under "Discover Business Insights", click on the drop-down arrow on "Explore this Data"--> choose "Auto Create Report" option. Power BI automatically generate a report base     on data in Your Semantic Model
##### Let's further build on the  Auto Created Report by drilling down on the data in your Semantic Model to build a dynamic report.
- Click on "Edit" tab at the top. Then, continue.
- At the bottom of the page, click on "+" to create a blank new page for our visuals.
- At the top of the New Page, click on "Open Data Model"
Let us create new Measures for  our Report using DAX to further analyze the Crypto Market. The DAX you would be creating shall be on "Sentiments Table" ("Positive sentiments", "Negative Sentiments" and "Neutral Sentiments") and Crypto Metric Table ("4 Days Moving Average", "Price Change 24h", "Total Market Cap" of all the 12 selected Cryptocurrencies and "Total Market Dominance" of each crypto currency, i.e. market share of each currency .

### Data Analysis Expression on Sentiments Table.
##### Steps:
- In your Semantic Model window, right click on the three dots "..." on your sentiments table.
- From the dropdown, click on "New Measure"
- Then, input the following DAX script for each of the measures and save
Negative Sentiment:
```
Negative Sentiment % = 
IF (
    COUNTROWS (FILTER ( 'sentiments', 'sentiments'[sentiment] = "negative" )) > 0,
    DIVIDE (
        CALCULATE (
            COUNTROWS(FILTER ( 'sentiments', 'sentiments'[sentiment] = "negative" ))
        ),
        COUNTROWS('sentiments')
    )*100,
    0
)

```
Positive Sentiment:

```
Positive Sentiment % = 
IF (
    COUNTROWS (FILTER ( 'sentiments', 'sentiments'[sentiment] = "positive" )) > 0,
    DIVIDE (
        CALCULATE (
            COUNTROWS(FILTER ( 'sentiments', 'sentiments'[sentiment] = "positive" ))
        ),
        COUNTROWS('sentiments')
    )*100,
    0
)

```
Neutral Sentiments:

```
Neutral Sentiment % = 
IF (
    COUNTROWS (FILTER ( 'sentiments', 'sentiments'[sentiment] = "neutral" )) > 0,
    DIVIDE (
        CALCULATE (
            COUNTROWS(FILTER ( 'sentiments', 'sentiments'[sentiment] = "neutral" ))
        ),
        COUNTROWS('sentiments')
    )*100,
    0
)

```

### Data Analysis Expression on Sentiments Table.
##### Steps:
- In your Semantic Model window, right click on the three dots "..." on your Crypto metric table. i.e. "tbl_cleaned_data"
- From the dropdown, click on "New Measure"
- Then, input the following DAX script for each of the measures and save

4 Days Price Moving Average:

```
4DayMovingAverage = 
CALCULATE(
    AVERAGE([Price]),
    DATESINPERIOD('tbl_cleaned_data'[Date], LASTDATE('tbl_cleaned_data'[Date]), -3, DAY)
)

``` 

Price Change_24h:

```
Price Change 24h = 
VAR PreviousPrice = 
    CALCULATE(
        MAX([Price]),
        DATEADD('tbl_cleaned_data'[Date], -1, DAY)
    )
RETURN
    DIVIDE(
        MAX([Price]) - PreviousPrice,
        PreviousPrice,
        BLANK()
    ) * 100

```

Total Market Cap :

```
Total Market Cap = SUM([Market_Cap])

```

Total Market Cap Dominance:

```
Total Market Cap Dominance = DIVIDE(
    [Total Market Cap],
    CALCULATE(SUM([Market_Cap]), ALL('tbl_cleaned_data')),
    0
) * 100

```
Then, close the Semantic Model.

- Then, go back to your dashboard to build a live report.Using the "Card" visual. Create three "Card" visuals for each of the sentiment measures created.
Page 1:
***** Image Power BI Automatic Created Report.
##### Page 2:***** Image
2a. Create a   Crypto_News table in the report by clicking on the the "table" visual to the top right, under visualization pane, you have an empty table in your canvas.
- Add required fields. First, expand the table by clicking on your table name, say"sentiments" under (Data) Title , to your top right. This reveals in your table as well as the newly created measures for the 
 "sentiment" table.
- Select the following fields/columns (Title, Provider, Url, Snippet, Date) to populate your table.
- Next, Create a Date Slicer by using the slicer visual under "visualisation Pane"
- Format the "Date" slicer to "drop-down" for capturing each date, to make your report organise by date.
- Filter the "News" Table and measures ("Postive sentiment", "Negative Sentiment", "Neutral Sentiment") cards by date, such that the dashboard by default will show the report by current date,with the option to 
  filter the report by previous date.
- Continue formatting your dashboard as deep as your creativity permits.
- Finally, remember to save your work.
*** Images

- 2b. Use the "Line Graph" visuals to visualize the 4 days "Price Moving Average" measure we created and "Price" .
- On the  Y-axis field, drag and drop "4 Days Moving Average" measure and "Price" metric While on the X-axis field, drag and drop the "date" column.

##### Page 3: Dynamic Crypto table showing key metrics *******Image
3. Create a Crypto_Currency table showing tthe top 12 cryptocurrencies and their corresponding statistics at a particular time daily.Click on the the "table" visual to the top right, under visualization pane, 
   you have an empty table in your canvas.
- Add required fields. First, expand the table by clicking on your table name, say"tbl_cleaned_data" under (Data) Title , to your top right. This reveals in your table as well as the newly created measures for 
  the "Crypto" table.
- Select the following fields/columns [Name, Price, Percent Change(24h), Volume, Market Cap, Total Supply, Circulating Supply, Fully Diluted Market Cap, Date) to populate your table.
- Next, Create a Date Slicer by using the slicer visual under "visualisation Pane"
- Format the "Date" slicer to "drop-down" for capturing each date, to make your report organise by date.
- Filter the "Crypto" Table by date, such that the dashboard by default will show the report by current date,with the option to filter the report by previous date.
##### Page 4.*****Image
- 4a. Create a "Total Market Cap Dominance By Currency by Currency" Using the Treemap Chart visual to explain the market share of each crypto currency in a pool o 12  crypto currencies.
- 4b. Create a "Total Market Capitalization " of the 12 top Crypto Currencies, using the Donot Chart.
- 4c. Create a "24h Change in Price " chart of the top 12 Crypto currencies using waterfall chart.


## Pipeline 1: Orchestration For Crypto Data Using Data Factory
Creating Pipeline using Data Factory to orchestrate everything that we have done so far in this end to end project.
- Go into your workspace
- Click on your Data Factory Pipeline
##### Orchestration:
- Drag and position the "Copy Data" to the left on the canvas.
- Click on "Notebook" at the top right.
- Connect the "Copy Data" to the Notebook, say  "Crypto Data" using "On Success"
- "General" tab --> "Name (Input: "Data Transformation")
- "Settings" tab --> "workspace"(from the drop-down, choose the name of your workspace)--> Then, "Notebook" (from the drop-down, choose the Notebook you used for data transformation)
#### Again.
- Click on "Notebook" at the top right.
- Connect the "Data Transformation" to the new Notebook say "cleaned Crypto Data" using "On Success"
- "General" tab --> "Name (Input: "Cleaned Crypto Data")
- "Settings" tab --> "workspace"(from the drop-down, choose the name of your workspace)--> Then, "Notebook" (from the drop-down, choose the Notebook you used for Sentiment Analysis)
Then, click save on your top-left, to save your pipeline
Then, run your pipeline.
##### Screen shot.

![Screenshot 2024-09-20 181104](https://github.com/user-attachments/assets/f30192d4-2052-4a13-b60f-635640dbf175)

Schedule Pipeline To Run Once Daily AT 6: 00 PM GMT + 1
The pipeline will be automatically triggered at 6: pm in the evening every day, ingesting the latest data on 12 selected crypto  currencies  and automatically updates the Power BI report with the latest data on crypto currencies.
##### Steps:
- In Data Factory canvas, click on "Schedule" button at the top.
- Check the radio button "ON" under Schedule Run.
- From "Repeat" drop-down, Pick "Daily" --To choose pipeline run frequency option.
- Under "Time", pick the time you want to schedule the pipeline to run, say 6:00 PM GMT +1
- Select the start date-time and end date-time of your schedule pipeline run from the "Start Date and Time" and "End Date and Time" calendar.
- "Time Zone" .You have the option of selecting your time zone, but the default is the time zone you are based on, so it's advisable to go with the default time zone.
-  Then, click "Apply"
##### Pipeline Monitor.
Go to Data Factory
- Click "View Run History" tab at the top.--You will see recent run of your pipeline. Better still you can proceed to
- "Go to Monitoring hub" at the bottom-left
- Then, click "Go to Monitoring hub"

## Pipeline 2: Orchestration For Crypto News & Opinions Using Data Factory
Creating Pipeline using Data Factory to orchestrate everything that we have done so far in this end to end project.
- Go into your workspace
- Click on your Data Factory Pipeline
##### Orchestration:
- Drag and position the "Copy Data" to the left on the canvas.
- Click on "Notebook" at the top right.
- Connect the "Copy Data" to the Notebook, say  "Crypto News" using "On Success"
- "General" tab --> "Name (Input: "Data Transformation")
- "Settings" tab --> "workspace"(from the drop-down, choose the name of your workspace)--> Then, "Notebook" (from the drop-down, choose the Notebook you used for data transformation)
#### Again.
- Click on "Notebook" at the top right.
- Connect the "Data Transformation" to the new Notebook say "Crypto News Sentiments" using "On Success"
- "General" tab --> "Name (Input: "Crypto News Sentiments")
- "Settings" tab --> "workspace"(from the drop-down, choose the name of your workspace)--> Then, "Notebook" (from the drop-down, choose the Notebook you used for Sentiment Analysis)
Then, click save on your top-left, to save your pipeline
Then, run your pipeline.
##### Screen shot.

![Screenshot 2024-09-20 185508](https://github.com/user-attachments/assets/95cef349-5991-4071-9b1d-a13860255271)

Schedule Pipeline To Run Once Daily AT 7: 00 PM GMT + 1
The pipeline will be automatically triggered at 7: pm in the evening every day, ingesting the latest news and opiniond on crypto  currencies  and automatically updates the Power BI report with the latest sentiments on crypto currencies.
##### Steps:
- In Data Factory canvas, click on "Schedule" button at the top.
- Check the radio button "ON" under Schedule Run.
- From "Repeat" drop-down, Pick "Daily" --To choose pipeline run frequency option.
- Under "Time", pick the time you want to schedule the pipeline to run, say 6:00 PM GMT +1
- Select the start date-time and end date-time of your schedule pipeline run from the "Start Date and Time" and "End Date and Time" calendar.
- "Time Zone" .You have the option of selecting your time zone, but the default is the time zone you are based on, so it's advisable to go with the default time zone.
-  Then, click "Apply"
##### Pipeline Monitor.
Go to Data Factory
- Click "View Run History" tab at the top.--You will see recent run of your pipeline. Better still you can proceed to
- "Go to Monitoring hub" at the bottom-left
- Then, click "Go to Monitoring hub"

## Data Activator Email Alert In Power BI
- Go to your workspace in Fabric.
- Power BI report
##### To configure your alert, you have to pick a visual upon which you want to configure the alert. In our case , we are picking the "Negative Sentiment %" card
- Click on the "Negative Sentiment %" card, under it click on three dots "..."
- From the drop-down, choose "set alert"
- On the right side, under "set an alert" --> "Visual" drop-down, pick the visual you want to set an alert on, say (Card 1)
- Under "Condition" --> 
   - "Measure": from the drop-down, pick the card you want to create alert on, say (Negative Sentiment %)
   - "Operators": from the drop-down, pick the 'operator' you want for your alert say (Become greater than)
   - "Value", Specify the numerical value you are using as you condition, say (00.00)
- Action --> (Outlook email or Teams message)pick one that is suitable to you, say (Outlook email)
- Click "show save option"
- Under "My Workspace" select your workspace name
- Under "item" click on "Create a new reflex item"
- Under "Item name" input your item name, say (Negative Sentiment Item)
- Then, click "Create" to create the alert.
- Then, click on "Open Data Activator" -- To find all the information regarding the alert created



















