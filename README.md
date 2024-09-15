# Business Case: Real-time Crypto Currency Performance and Sentiment Analysis Dashboard
# Executive Summary
This business case proposes the development of a real-time dashboard that provides comprehensive insights into the performance and sentiment surrounding the top  cryptocurrencies. By leveraging advanced data analytics tools and APIs, this dashboard will empower stakeholders with critical information to make informed decisions in the volatile cryptocurrency market.

## Problem Statement
The cryptocurrency market is characterized by rapid price fluctuations, evolving regulatory landscapes, and diverse investor sentiment. Lack of access to real-time, comprehensive data can lead to suboptimal investment decisions and missed opportunities.

## Proposed Solution
The proposed solution involves the following steps:
- Data Extraction: Utilize the CoinMarketCap API to collect live data on the top cryptocurrencies, including market capitalization, trading volume, price, and other relevant metrics. As well as leverage Google 
  Custom Search Engine API to collect latest information, news,opinions and insightson the crypto market.
- Data Transformation: Employ Synapse Data Engineer in Microsoft Fabric to transform and cleanse the extracted data, ensuring data quality and consistency.
- Sentiment Analysis: Leverage the Google CSE JSON API to extract daily news and opinions related to the top  cryptocurrencies. Perform sentiment analysis using Synapse Data Science to gauge market sentiment and 
  identify emerging trends.
- Dashboard Development: Create a dynamic dashboard in Power BI that visualizes key performance indicators (KPIs) for each cryptocurrency, including price charts, trading volume trends, and sentiment analysis 
  results.
- Data Activator: To configure  email alerts in Power BI visuals to predict market sentiments shaped by latest news, opinions and releases in the digital asset space.
- Orchestrate the whole process as an End-to-End Pipeline using Microsoft Fabric- Data Factory.

## Benefits
- Real-time Insights: Access up-to-date information on cryptocurrency performance and sentiment.
- Informed Decision-Making: Support investment decisions based on data-driven insights.
- Risk Mitigation: Identify potential risks and opportunities by monitoring market trends.
- Competitive Advantage: Gain a competitive edge by having access to in-depth market intelligence.

## Technical Approach
- Data Sources: CoinMarketCap API, Google CSE JSON API
- Data Ingestion: Microsoft Fabric Data Factory
- Data Transformation: Microsoft Fabric Synapse Data Engineer
- Sentiment Analysis: Micro Fabric Synapse Data Science
- Dashboarding: Power BI

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











