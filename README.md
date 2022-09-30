# Malaria in Africa

This is the analysis carried out for my Coursera Google Data Analysis Project. It analyzes malaria trends in Africa from 2007-2017. It also checks for the correlation between the number of malaria cases reported and the percentage of people with access to basic clean water and sanitation.


## Authors

- [@essiee1](https://www.github.com/essiee1)


## Date: 30th September, 2022

## [Tableau Dashboard](https://public.tableau.com/app/profile/esohe.okuomose/viz/MalariainAfrica_16644876261550/Dashboard1#1)
## Introduction

This case study follows the 6 steps of data analysis:

### Ask
### Prepare
### Process
### Analyze
### Share
### Act
## Scenario

Africa is the second largest continent in the world. It also has the greatest malaria burden worldwide, especially the Sub-Saharan Africa. According to the World Health Organization, the estimated number of malaria deaths stood at 627,000 in 2020. Africa was home to 95% of the malaria cases and 96% of deaths. A major risk factor for this disease is poor environmental sanitation as this can provide a breeding ground for the mosquitoes.
In this case study, we would be studying the trend of malaria in Africa from 2007-2017. We would also get insights on the correlation between the cases of malaria reported and the percentage of people with access to basic clean water and sanitation.

## Ask

Analyze data to check the trend of malaria in Africa from 2007-2017. Also get insights on the correlation between the cases of malaria reported and the percentage of people with access to basic clean water and sanitation.

## Prepare

Data Source: Malaria in Africa Dataset from [Kaggle](https://www.kaggle.com/datasets/lydia70/malaria-in-africa)

The data also follows the ROCCC approach:

#### Reliability
The data is from the world bank data source collected from all African countries between 2007-2017.

#### Original
The data on malaria incidence, malaria cases reported and women on Intermittent Malaria Preventive Therapy were retrieved from the world bank open data source. The longitude and latitude data were manually uploaded by the owner of the dataset.

#### Comprehensive
The data is not comprehensive as some of the columns have empty cells.

#### Current
Data is not current as it was uploaded 2 years ago and it was collected from 2007-2017.

#### Cited
Unknown

The data has some limitations due to the number of empty columns.

 

## Process

The data was cleaned using Microsoft Excel. The dataset was duplicated and analysis began with the duplicate dataset.

The data was examined and nulls were noticed. Columns with a large number of nulls were removed as they had no relevance to the insights needed.

Also, duplicates were checked for of which there was no duplicate.

The columns were renamed to a more convenient format and the data was uploaded to the SQL server for analysis.
## Prepare

Data Source: Malaria in Africa Dataset from [Kaggle](https://www.kaggle.com/datasets/lydia70/malaria-in-africa)

The data also follows the ROCCC approach:

#### Reliability
The data is from the world bank data source collected from all African countries between 2007-2017.

#### Original
The data on malaria incidence, malaria cases reported and women on Intermittent Malaria Preventive Therapy were retrieved from the world bank open data source. The longitude and latitude data were manually uploaded by the owner of the dataset.

#### Comprehensive
The day is not comprehensive as some of the columns have empty cells.

#### Current
Data is not current as it was uploaded 2 years ago and it was collected from 2007-2017.

#### Cited
Unknown

The data has some limitations due to the number of empty columns.

 

## Analyze

Sum of total malaria Incidence Reported between 2007-2017 was 587,581,549

```
SELECT SUM(malaria_cases_reported)
FROM malaria
```

To calculate the total incidence of malaria per 100 of the population from 2007-2017. The sum gotten was 104,548.

```
SELECT SUM(malaria_incidence)
FROM malaria
```

Next, we look at the progression of the incidence of malaria in Africa from 2007-2017. 

```
SELECT country, year, malaria_incidence
FROM malaria
ORDER BY malaria_incidence ASC
```

After running this code, we found that the year with the highest incidence of malaria per 1000 of the population was 2007 and the least was 2017 with a sum of 10,508 and 8,816 respectively. There is a steady decrease over the years although an increase was observed in 2016 compared to the previous 3 years.


Next, we focus on the incidence of malaria per 1000 of the population in Nigeria, a country in West Africa. 

```
SELECT country, year, malaria_incidence
FROM malaria
WHERE country IN 'Nigeria'
ORDER BY malaria_incidence DESC
```

The year with the highest incidence of malaria per 1000 was 2008 with a value of 424.7 and the least was 2016 with a value of 281.4. There is also a general steady decrease through the years and this shows a positive progress in the eradication of malaria.


For the next insight, we look at the countries with the highest incidence of malaria which is the most recent year in the data set.

```
SELECT country, year, incidence_of_malaria
FROM malaria
WHERE year = 2017
ORDER BY incidence_of_malaria DESC
```

In the year 2017, the country with the highest incidence of malaria per 1000 of the population was Rwanda with a value of 538.3 per 1000. This means in every 1000 persons, 538.3 persons had malaria. This is on the high side as it is more than half of the population. Further personal research showed that Rwanda, country in the Sub-Saharan Africa region has had a high malaria burden over the years. This country is followed by Liberia and Burkina  Faso with values of 401.1 and 399.9 respectively. 


Back to the analysis, the year with the highest cases of malaria reported was checked for.

```
SELECT country, year, malaria_cases_reported
FROM malaria
WHERE year = 2017
ORDER BY malaria_cases_reported DESC
```

From the result gotten from running this code, we find out that it is opposed to the results gotten from the incidence of malaria. The year with the highest number of cases reported was 2017 with a value of 128,146,255. The year with the least reported cases was 2008 with the value 9,508,374. This shows that there has been a steady increase over the years. This could mean that more persons now have access to health care facilities where they can easily go to see a medical practitioner to report their symptoms and get proper care.


Now, we'll be comparing the percentage of the population who have access to basic clean water with the number of malaria incidence reported per country.

```
SELECT country, basic_water, malaria_cases_reported
FROM malaria
WHERE basic_water NOTNULL
ORDER BY basic_water ASC
```


NOTNULL was used because from the initial analysis, 2 countries had a blank space in the basic_water column.
From this analysis, the countries with zero reported cases of malaria had an access to basic clean water from 95% and above. These countries included Libya, Egypt, Ethiopia and Morocco. We can therefore say that there is a correction between these 2 factors. Democratic Republic of Congo had the least access to basic clean water with less than half of the total population percentage having access to basic clean water.


Lastly, we'll be comparing the percentage of the population who have access to basic sanitation with the number of malaria incidence reported per country.

```
SELECT country, basic_sanitation, malaria_cases_reported
FROM malaria
WHERE basic_sanitation NOTNULL
ORDER BY basic_sanitation ASC
```

This analysis gave the same response as that of basic clean water. More insight is gotten from the Tableau visualization. 
## Share

[Tableau Visuslization](https://public.tableau.com/app/profile/esohe.okuomose/viz/MalariainAfrica_16644876261550/Dashboard1#1)

## Act

Although the incidence of malaria in Africa is reducing, it is still on the high side. Seeing that there is a relationship (although not absolute) between malaria cases and access to clean water and sanitation, countries should increase the percentage of people with access to basic sanitation and clean water in order to see a decline in the malaria cases in their countries.

