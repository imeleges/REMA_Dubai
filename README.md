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
It is not straight forward for a newcomer to Dubai to understand how prices are assigned to listings. E.g. at first glance several listings of studio and 1 bedroom apartments in the given two areas of Dubai have approximately same yearly price.  

Questions to answer:  
 - How many options are there for different number of bedrooms? 
 - How do studio, 1 and 2 bedroom flats differ in their square areas, features if prices seem close?
 - What buildings have best combination of location, flat square area and price? 
 - ...


All data was scraped from **Bayut** website on **August 9, 2022** and saved as **.CSV** file.

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

In this Dataset, we have information for **4800+** apartments available for rent in Downtown Dubai and DIFC areas in August 2022 and having different parameters like:  
*price, address, number of bedrooms, area in sqft, description, building info, amenities, etc.*

<p align="center">
	<img src="https://github.com/imeleges/REMA_Dubai/blob/main/img/dataframe.png?raw=true">
	<sub>Dataset preview</sub>
</p>


### Dataset Glossary (Column-Wise)

`price` -  Listed in AED  
`address` - Including the name of the building or/and complex, district, city  
`beds` - Number of bedrooms  
`baths` - Number of bathrooms  
`area-sqft` - Area of the apartment in square feet  
`description-title` - Title of a listing  
`description` - Description with a lot of additional information  
`reference-no` - Reference number on the website  
`date-added` - Publishing date includes Day, Month and Year  
`balcony-size-sqft` - Area of the balcony in square feet  
`parking` - Yes/No   
`building-info-name` - Unique building name  
`building-info-floors` - Number of levels (floors) in the building  
`building-info-year` - Year when the building was constructed   
`building-info-area-sqft` - Total building area in square feet  
`furnishing` - Furnished/Unfurnished   
`features-amenities` - Additional features  


<details>
<summary>Dropped columns (click to expand)</summary>

Those columns were dropped at the beginning of analysis

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

- Many columns contained **missing values** (e.g. number of bathrooms, balcony size, building info, furnishing, etc.) Some have only a few missing, others, many and so those were either filled out with info that is missing or the column was be dropped altother as it doesn't bring value.
- **Data types** were changed to decrease memory usage, e.g price column and area converted from object (text) to number and date column - from object to date type.  
- All columns were renamed and filled with relevant values.

***

### Exploratory Data Analysis

Below is data analysis using visual techniques to discover trends, patterns, or to check assumptions with the help of statistical summary and graphical representations.

#### Adding new features

Data enrichment step here is to append or enhance collected data with relevant context obtained from other columns.

`Address` - column containing listing's address was split into columns: city, area, building name and tower complex name.  
`Date` - column was split into four: Year, Month, Day and Weekday   
`Price per square foot` - calculated from listing price divided by the apartment area  
Text containing columns title, description and features/amenities contain some keywords that were converted to new features:  
`Chiller` - assigned **1** when chiller is free, **0** otherwise. Same for `Parking`, `Bills`  


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

Outliers start from price 500,000 and spread up to 3,000,000. Most likely it's a huge apartment with many rooms and that is more luxurious or it's simply a typo in numbers.

<p align="center">
	<img src="https://github.com/imeleges/REMA_Dubai/blob/main/img/prices_logs.png?raw=true">
	<sub>Log scaled prices</sub>
</p>

Logarithmically scaled prices displaying data over a very wide range of values in a compact way.

<p align="center">
	<img src="https://github.com/imeleges/REMA_Dubai/blob/main/img/prices_700_000.png?raw=true">
	<sub>Prices up to 700,000</sub>
</p>

The look into more common range of prices for every number of bedrooms shows that majority of all listings are between 90,000 and 300,000 AED. With a very noticeable spike for one bedroom apartments at approximately 100,000 AED.

<p align="center">
	<img src="https://github.com/imeleges/REMA_Dubai/blob/main/img/all_bdr_prices_boxplot.png?raw=true">
	<sub>Prices boxplot</sub>
</p>

Boxplot graphically demonstrates the locality, spread and skewness groups of prices for every number of bedrooms. This diagram indicates variability outside of the upper and lower quartiles.  

One very noticeable thing is that four-bedroom apartments not only have huge interquartile range, but also very long whiskers on both sides, where left whisker overlaps with median price of three-bedroom listings. This could be another typo in listings, or possibly smaller total area or maybe a building on the edge of the district.

Interestingly interquartile range for studios and 1 bedroom apartments is almost the same. Boxplot for studios has a nearly normal distribution, where 1 bedroom listings' distribution has a slightly heavier right tail. That discovery raises a new question, why to rent a studio if it's in the same price range as one bedroom listings. Perhaps those studios has larger areas.  


#### Area

Area range: 
- start at minimum of 37 sqft
- and goes up to 6,792 sqft,
- with median value of  1346 sqft.

Area of 37 sqft is obviously a typo, that couldn't be so small, and maximum areas is could be a misplaced listing and supposed to be in other category, commercial like offices, shop, etc.

<p align="center">
	<img src="https://github.com/imeleges/REMA_Dubai/blob/main/img/area_4_500.png?raw=true">
	<sub>Area in sqft up to 4,500</sub>
</p>

On the diagram above difference in total areas is clearly visible, with just a minor overlap of 1,700-2,000 sqft for 2 and 3 bedroom apartments.  

<p align="center">
	<img src="https://github.com/imeleges/REMA_Dubai/blob/main/img/all_bdr_area_boxplot.png?raw=true">
	<sub>Area of each bedroom boxplot</sub>
</p>

Even though there're some studios with area above 750 sqft, still most of them are well apart from 1 bedroom listings.

#### Bedrooms

After all data preprocessing there're 4,802 apartments left, listed below grouped by number of bedrooms:  

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
For current tasks in this project on the next steps will be reviewed apartments for 1 and 2 bedrooms listings. 

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