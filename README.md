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
- Data Activator: To configure  email alerts in Power BI visuals to predict market sentiments shaped by latest news, opinions and releases in the digital asset 
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
- Dashboarding: Power BI in Microsoft Fabric

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

#### Crypto Data
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

#### Crypto News & Opinins
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

#### Crypto Data
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


#### Crypto News & Opinions
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

#### Handling Incrementa Loading

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

















