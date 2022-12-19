# REMA Dubai

## Residential Rental Real Estate Market Analysis in Dubai, UAE.

**DIFC** (Financial Centre) and **Downtown** areas apartments analysis.

[![Data Analyst](https://img.shields.io/static/v1?label=trend&message=Data%20Analyst&color=218c74)](#) [![Data Scientist](https://img.shields.io/static/v1?label=trend&message=Data%20Scientist&color=706fd3)](#)  

[![Pandas](https://img.shields.io/static/v1?label=tool&message=Pandas&color=40407a)](#) 
[![Python](https://img.shields.io/static/v1?label=tool&message=Python&color=33d9b2)](#) 
[![Matplotlib](https://img.shields.io/static/v1?label=tool&message=Matplotlib&color=706fd3)](#) 
[![Scikit-learn](https://img.shields.io/static/v1?label=tool&message=Sklearn&color=ff793f)](#) 
[![Seaborn](https://img.shields.io/static/v1?label=tool&message=Seaborn&color=ff5252)](#)  

[![Data visualization](https://img.shields.io/static/v1?label=skill&message=Data%20visualization&color=F97F51)](#) 
[![Exploratory data analysis](https://img.shields.io/static/v1?label=skill&message=Exploratory%20Data%20Analysis&color=82589F)](#) 
[![Data preprocessing](https://img.shields.io/static/v1?label=skill&message=Data%20Preprocessing&color=B33771)](#)  

**Problem statement:**  
It is not straight forward for a newcomer to Dubai to understand how prices are assigned to listings. E.g. at first glance several listings of studio and 1 bedroom apartments in the given two areas of Dubai have approximately same yearly price while square area is quite different. Is studio a good value for its money in comparison to 1 bedroom flat?

Questions to answer:  
 - How many options by number of bedrooms are there to choose from? 
 - Do studios, 1 and 2 bedroom flats differ significantly in their square areas and features, what is different about them?
 - ...
  - ...


Data was scraped from **Bayut** website on **August 9, 2022** and saved as **.CSV** file.

## Table of contents
- [About Dataset](#about-dataset)
	- [Content](i#content)
	- [Dataset Glossary](#dataset-glossary-column-wise)
- [Data preprocessing](#data-preprocessing)
- [Exploratory Data Analysis](#exploratory-data-analysis)
	- [Adding new features](#adding-new-features)
	- [Number of uniques per feature](#number-of-unique-values-per-feature)
	- [Prices](#prices)
	- [Area](#area)
	- [Bedrooms](#bedrooms)
- ...


## About Dataset

### Content

In this dataset we have information about **4800+** apartments available for rent in Downtown and DIFC areas of Dubai in August 2022. Listing have different parameters like:  
*rental price, address, number of bedrooms, area in sq.ft., description, building info, amenities, etc.*

<p align="center">
	<img src="https://github.com/imeleges/REMA_Dubai/blob/main/img/dataframe.png?raw=true">
	<sub>Dataset preview</sub>
</p>


### Columns / Features

`price` -  Listed in AED  
`address` - Including the name of the building or/and complex, district, city  
`beds` - Number of bedrooms  
`baths` - Number of bathrooms  
`area-sqft` - Area of the apartment in square feet  
`description-title` - Title of the listing  
`description` - Additional information  
`reference-no` - Reference number on the website  
`date-added` - Publishing date (day, month and year)  
`balcony-size-sqft` - Area of the balcony in square feet  
`parking` - Yes/No   
`building-info-name` - Building name  
`building-info-floors` - Building hight in number of floors  
`building-info-year` - Year when the building was constructed   
`building-info-area-sqft` - Total building area in square feet  
`furnishing` - Furnished/Unfurnished   
`features-amenities` - Additional building/flat features  


<details>
<summary>Dropped columns (click to expand)</summary>

These columns were dropped at the beginning of analysis:

`apartmet-link-href` -  unnecessary for analysis   
`rent-frequency` - only Yearly listings were parsed  
`web-scraper-order` -  unnecessary for analysis   
`web-scraper-start-url` -  unnecessary for analysis   
`pagination` -  unnecessary for analysis   
`apartmet-link` -  unnecessary for analysis but could be added back later   
`building` -  only one name value and the rest is missing values  

</details>

*** 

### Data preprocessing
What was done:
- Many columns contained **missing values** (e.g. number of bathrooms, balcony size, building info, furnishing, etc.) Some had only a few values missing while others a lot. Thos were either filled or the column was dropped altother as it didn't bring value.
- **Data types** were changed to decrease memory usage, e.g price and area columns were converted from object (text) to number and date column - from object to date type.  
- All columns were renamed and blanks were filled with relevant values.

***

### Exploratory Data Analysis

Below is data analysis using visualization to discover trends and patterns, and validate hypothesises.

#### Adding new features

Data enrichment step here is to append or enhance collected data with relevant context obtained from other columns.

`Address` - column containing listing address was split into columns: city, area, building name and tower complex name.  
`Date` - column split into Year, Month, Day and Weekday.   
`Price per square foot` - calculated from listing rental price divided by the area.  
Text containing listing title, description and features/amenities contains keywords some of which were converted into new features:  
`Chiller` - assigned **1** when chiller is free, **0** otherwise. Same for `Parking` and `Bills`.

#### Number of unique values per feature

<p align="center">
	<img src="https://github.com/imeleges/REMA_Dubai/blob/main/img/num_of_uniq_pfeature.png?raw=true">
	<sub>Number of unique values per feature</sub>
</p>

On the diagram above some columns have a high number of unique values ex. **759 options for area in sqrt** while others have much fewer variations ex. **chiller free Yes/No**

#### Prices 

Prices range: 
- start at minimum of 40,000 AED 
- and goes up to 3,000,000 AED, 
- with median value of 180,000 AED.

<p align="center">
	<img src="https://github.com/imeleges/REMA_Dubai/blob/main/img/prices_all.png?raw=true">
	<sub>Prices for all listings</sub>
</p>

Outliers start from price 500,000 and spread up to 3,000,000. Most likely it's a huge apartment with many rooms and that is more luxurious or it's an error.<br><br>

<p align="center">
	<img src="https://github.com/imeleges/REMA_Dubai/blob/main/img/prices_logs.png?raw=true">
	<sub>Log scaled prices</sub>
</p>

Logarithmically scaled prices display data over a very wide range of values in a compact way.<br><br>

<p align="center">
	<img src="https://github.com/imeleges/REMA_Dubai/blob/main/img/prices_700_000.png?raw=true">
	<sub>Prices up to 700,000</sub>
</p>

Look into most common range of prices for every number of bedrooms shows that majority of all listings are between 90,000 and 300,000 AED. With a very noticeable spike for one bedroom apartments at approximately 100,000 AED. This means with budget of 100k there's a much higher number of one bedroom options to choose from than with budget even 5k lower. Also adding nother 5k would not increase number of options much.<br><br>

<p align="center">
	<img src="https://github.com/imeleges/REMA_Dubai/blob/main/img/all_bdr_prices_boxplot.png?raw=true">
	<sub>Prices boxplot</sub>
</p>

Boxplot demonstrates spread and skewness of rental prices by number of bedrooms. This diagram indicates variability outside of the upper and lower quartiles.  

One very noticeable thing is that four-bedroom apartments not only have huge interquartile range, but also very long whiskers on both sides, where left whisker overlaps with median price of three-bedroom listings. This could be another error, possibly smaller total area or a building on the edge of the district.

Interestingly interquartile range for studios and 1 bedroom apartments is almost the same. Studios prices have nearly symmetrical distribution, while 1 bedroom listings distribution has a heavier right tail. That discovery raises a new question, why rent a studio if it's in the same price range as one bedroom listings? Perhaps those studios has larger areas, are located in more prestigious buildings or are furnished. At teh same time, if lower rental price is a prioriy, rgere are studios to choose from. 


#### Area

Area range: 
- start at minimum of 37 sq.ft.,
- and goes up to 6,792 sq.ft.,
- with median value of 1,346 sq.ft.

Area of 37 sq.ft. is obviously an error. Largest areas could be an error too or a misplaced listings that were supposed to be under a commecial category (offices, shops, etc).

<p align="center">
	<img src="https://github.com/imeleges/REMA_Dubai/blob/main/img/area_4_500.png?raw=true">
	<sub>Area in sq.ft. up to 4,500</sub>
</p>

On the diagram above difference in total areas is clearly visible, with just a minor overlap of 1,700-2,000 sq.ft. for 2 and 3 bedroom apartments.<br><br>

<p align="center">
	<img src="https://github.com/imeleges/REMA_Dubai/blob/main/img/all_bdr_area_boxplot.png?raw=true">
	<sub>Area of each bedroom boxplot</sub>
</p>

Even though there're some studios with area above 750 sq.ft., still most of them are well apart from 1 bedroom listings.
Interesting fact: areas have less ranges in each category which makes sense - apartments in tall buildings tend to be alike by size and floorplan.
Another thing is that areas are much more apart from one another than rental prices which means price heavily depends on additional facts, not square area alone.

#### Bedrooms

After all data preprocessing there're 4,802 listings left:  

- Studio: 435
- 1 Bedroom: 1474
- 2 Bedrooms: 1983
- 3 Bedrooms: 832
- 4 Bedrooms: 75
- 5 Bedrooms: 3

<p align="center">
	<img src="https://github.com/imeleges/REMA_Dubai/blob/main/img/number_of_bdrs.png?raw=true">
	<sub>Number of bedrooms</sub>
</p>

**TOP-3** most listed options would be 2, 1 and then 3-bedroom apartments respectively.  

***

## 1 & 2 bedroom apartments analysis
For further analysis only 1 and 2 bedroom listings will be reviewed.

Earlier, while [checking for unique values](#number-of-unique-values-per-feature), **2204** were found in the description and **2219** by the description title. Manual processing would be time consuming, so finding most commonly used words / phrases would be much more efficient. TOP-30 phrases should be enough.

<p align="center">
	<img src="https://github.com/imeleges/REMA_Dubai/blob/main/img/wordclouds.png?raw=true">
	<sub>Word cloud for description (left) & description title (right)</sub>
</p>

There are few common phrases such as `Real Estate`, `Burj Khalifa`, `Downtown` and etc. that should be ignored as they bring no value.  
Meanwhile useful phrases like `Fully Furnished`, `Fitted Kitchen`, `Chiller free`, `Swimming pool`, `Bills included` etc. may affect prices, so could be useful.

### Prices

|Prices range |1 Bedroom| 2 Bedrooms|
|:--- | :---: | :---:|
|Count|1,474|1,983|
|Min|59,998|76,990|
|Median|115,000|225,000|
|Max|280,000|600,000|


<p align="center">
	<img src="https://github.com/imeleges/REMA_Dubai/blob/main/img/1_2_bdr_prices.png?raw=true">
	<sub>1 & 2 bedroom prices from 60,000 to 450,000</sub>
</p>

In the most common range of prices from 60,000 to 450,000, 1-bedroom apartments are concentrated between 80,000 and 130,000, where 2-bedrooms are distributed much wider across the range.

...

***
<!-- 
### Trends
[![Data Analyst](https://img.shields.io/static/v1?label=trend&message=Data%20Analyst&color=218c74)](#)
[![Data Scientist](https://img.shields.io/static/v1?label=trend&message=Data%20Scientist&color=706fd3)](#)

### Tools and Skills
[![Pandas](https://img.shields.io/static/v1?label=tool&message=Pandas&color=40407a)](#) 
[![Python](https://img.shields.io/static/v1?label=tool&message=Python&color=33d9b2)](#) 
[![Matplotlib](https://img.shields.io/static/v1?label=tool&message=Matplotlib&color=706fd3)](#) 
[![Scikit-learn](https://img.shields.io/static/v1?label=tool&message=Sklearn&color=ff793f)](#) 
[![Seaborn](https://img.shields.io/static/v1?label=tool&message=Seaborn&color=ff5252)](#)  

[![Data visualization](https://img.shields.io/static/v1?label=skill&message=Data%20visualization&color=F97F51)](#) 
[![Exploratory data analysis](https://img.shields.io/static/v1?label=skill&message=Exploratory%20Data%20Analysis&color=82589F)](#) 
[![Data preprocessing](https://img.shields.io/static/v1?label=skill&message=Data%20Preprocessing&color=B33771)](#)  

***
 -->