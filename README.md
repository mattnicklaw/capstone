# Capstone

## Executive Summary
I have moved around the U.S. my whole life. I have lived in 7 states and 19 counties in
my 40 years. I’ve lived in rural areas and the biggest cities in the country. So, I set out
to try to compare Quality of Life and Life Expectancy against Population Density.
I was excited to break down these demographics by county, to see snapshots of where
the Quality of Life in America is the best.

## Motivation
Being a nomad for most of my life, I have seen a lot America. I’ve lived by the coast,
and inland. In red states and in blue. Rich/poor, all of the above. With my background,
I feel like I have a unique take on what different parts of the U.S. are like. So I wanted to
tackle the United States by county and see if I can gain insight on where people live the
best quality of lives and longest lives(or both if there is a correlation).

## Data Question
“Is your Quality of Life affected by the population density surrounding you?”
Specifically, where do Americans live their best life? Are there any trends with high
(or low) density areas and Quality of Life? Is there a sweet spot somewhere in the
middle? 

## Quality of Life Breakdown
1. Percentage of adults reporting fair or poor health
2. The Average number of physically unhealthy days reported in the last month
3. The Average number of mentally unhealthy days reported in the last month
4. Low birthweight (which is a major factor in Life Expectancy)

## Data Sources
* [University of Wisconsin Population Public Health Institute](https://www.countyhealthrankings.org/explore-health-rankings/county-health-rankings-model)
* [The Current County and Equivalent National Shapefile - TIGER/LINE](https://catalog.data.gov/dataset/tiger-line-shapefile-2019-nation-u-s-current-county-and-equivalent-national-shapefile)

## The Process  
<details>
  <summary>Acquiring the data</summary>

After having found all 50 states (.CSV) on the County Health Rankings site, I used python to create a mega-merge to get all of this info into one easy-to-digest table. While the data was fairly clean, there was quite a bit of reformatting needed in order for the columns to match up for the merge that I wanted. 
</details>  

<details>
  <summary>Analyzing the data</summary>
  
I was missing SQL pretty bad at this point, so I installed a python package called PANDASQL, so I could manipulate my dataframes using SQL techniques.  From there I narrowed down my dataframes to find the states with the strongest and weakest correlations to Quality of Life, to analyze what affected that statistic the most. Starting with Population Density, I quickly realized there was no correlation, so I moved on to Percent Access to Exercise.  There was some correlation there, but not enough to wow anyone, so then I started diving into Percent of Adults with Some College, before finally finding Median Household Income as the #1 factor in determining Quality of Life on a county-by-county basis.

<details>
  <summary>Mapping</summary>

Using the TIGER/LINE shapefile I was able to get every county in the United States mapped with geospatial.  These county polygons were shaped using the geometry coordinates, and centroids found within. From there I broke it down state-by-state to find the biggest discrepencies (or similarities) between Quality of Life statistics, Density, Percent Access to Exercise, Percent Access to College, and finally Median Household Income.  I used a spectral color scheme heatmap to illustrate the difference in the above categories.

</details>
