# REMA Dubai

## Real Estate Market Analysis in Dubai, UAE.

Analysis of apartments in two areas **DIFC** (Financial Centre) and **Downtown**.

All data was scraped from **Bayut** website on August 9 and saved as **.CSV** file.

## Table content
- [About Dataset](#about-dataset)
	- [Content](i#content)
	- [Dataset Glossary (Column-Wise)](#dataset-glossary-column-wise)
- ...


## About Dataset

### Content

In this Dataset, we have information on almost 4800+ apartments available for rent with different parameters like price, address, beds, baths, area-sqft, description-title, description, reference-no, date-added, balcony-size-sqft, parking, building-info-name, building-info-floors, building-info-year, building-info-area-sqft, furnishing, features-amenities.

<p align="center">
	<img src="https://github.com/imeleges/REMA_Dubai/blob/main/img/dataframe.png?raw=true">
	<sub>Dataset</sub>
</p>


### Dataset Glossary (Column-Wise)

`price` -  Listed in AED  
`address` - Including the name of the building or/and complex, district, city  
`beds` - Number of bedrooms  
`baths` - Number of bathrooms  
`area-sqft` - Area of the apartment in square foot  
`description-title` - Title of a listing  
`description` - Description with lots of additional information  
`reference-no` - Reference number on the website  
`date-added` - Publishing date includes Day, Month and Year  
`balcony-size-sqft` - Area of the balcony in square foot  
`parking` - Yes/No   
`building-info-name` - Unique building name  
`building-info-floors` - Number of levels (floors) in the building  
`building-info-year` - Year when the building was constructed   
`building-info-area-sqft` - Total building area in square foot  
`furnishing` - Furnished/Unfurnished   
`features-amenities` - Additional features  


<details>
<summary>Those columns were dropped at the beginning</summary>

`apartmet-link-href` -  unnecessary for analysis   
`rent-frequency` - It only contains Yearly listings  
`web-scraper-order` -  unnecessary for analysis   
`web-scraper-start-url` -  unnecessary for analysis   
`pagination` -  unnecessary for analysis   
`apartmet-link` -  unnecessary for analysis but could be merged later   
`building` -  Has only one specific name and the rest is NaN  

</details>

***

**Trends**  
[![Data Analyst](https://img.shields.io/static/v1?label=trend&message=Data%20Analyst&color=218c74)](#)
[![Data Scientist](https://img.shields.io/static/v1?label=trend&message=Data%20Scientist&color=706fd3)](#)

**Tools and Skills**  
[![Pandas](https://img.shields.io/static/v1?label=tool&message=Pandas&color=40407a)](#) 
[![Python](https://img.shields.io/static/v1?label=tool&message=Python&color=33d9b2)](#) 
[![Matplotlib](https://img.shields.io/static/v1?label=tool&message=Matplotlib&color=706fd3)](#) 
[![Scikit-learn](https://img.shields.io/static/v1?label=tool&message=Sklearn&color=ff793f)](#) 
[![Seaborn](https://img.shields.io/static/v1?label=tool&message=Seaborn&color=ff5252)](#)  

[![Data visualization](https://img.shields.io/static/v1?label=skill&message=Data%20visualization&color=F97F51)](#) 
[![Exploratory data analysis](https://img.shields.io/static/v1?label=skill&message=Exploratory%20Data%20Analysis&color=82589F)](#) 
[![Data preprocessing](https://img.shields.io/static/v1?label=skill&message=Data%20Preprocessing&color=B33771)](#)  

***
