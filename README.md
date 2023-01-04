# Capstone

## Executive Summary
I have moved around the U.S. my whole life. I have lived in 7 states and 19 counties in
my 40 years. I’ve lived in rural areas and the biggest cities in the country. So, I would
like to try to compare Quality of Life and Life Expectancy against Population Density.
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
* [Google Sites](https://workspace.google.com/products/sites/)

## Analytic Process  
#### Acquiring the data  
-Note about qcor challenges, Selenium used  
-Note about attempt to obtain API for HRSA site
-Note about API for SAHIE providing older data only
-Challenges narrowing down what to include
## The Process  
<details>
  <summary>Acquiring the data</summary>

The first real challenge for this project was scraping details about the healthcare facilities that have met specific, federally defined criteria and serve as major players in providing rural (and other vulnerable populations) with care. Most of the data about most of the facilities could actually be obtained fairly easily from the Health Resources and Services Administration (HRSA) data site, but one key element, the ownership type for each facility, is not included in their data sets. To get that detail, along with information about a few additional facilities, I had to go to qcor.cms.gov. This site provides data about facilities certified by the Centers for Medicare and Medicaid Services (CMS), and let's just say it is not the most streamlined system I've ever encountered with details about each facility only available via individual pop-up windows.

This challenge provided the opportunity to use python along with Selenium web driver to navigate to each pop-up then scrape all relevant information before moving on to the next facility. Once I had this script up and running, it was easy to iterate through all the facility types of interest and grab the details I was after.

I had hoped to use APIs to obtain the bulk of the rest of my data, but I ran into a few hurdles. First, HRSA never responded to my requests to obtain an API, so I ended up just utilizing the tools on the site to search for and download additional data about healthcare facilities to pair with what I scraped from Qcor, and also to obtain details about Health Care Provider Shortage(HPSA) designations. The HRSA uses specific US Census poverty data as part of the process for scoring HPSAs, so for consistency, I also pulled this dataset from the HRSA site.

While I did find a way to obtain health care insurance coverage data via API, the data available using this method was a few years out of date, so again I ended up finding and downloading more current data from the US Census Bureau.

There are many other demographic and health metrics I was (and still am) curious to explore and potentially incorporate, but in the interest of maintaining a focus on the key pieces emphasized by my friend who works in this realm, I leave those additional pieces to possible future versions!
</details>  

<details>
  <summary>Cleaning and organizing the data</summary>

The main challenge related to cleaning the data involved making sure that all facility and HPSA entries included correct and consistent information about the county in which each was located and the rural status of that county. I found a data set listed a county name for every zip code, created a dictionary, and utilized it to fill in any missing county entries. From there, I used the rural status information defined for all HPSAs to fill in any missing/inconsistent facility-level data. There was also some work to most effectively combine the facility data sets from both Qcor and the HRSA site.

Once those pieces were in place, the focus was on consistent formatting for all three facility-level tables and filtering the other data sets down to just the those entries that are relevant for Tennessee.

</details>

<details>
  <summary>Loading data to Tableau, building dashboards</summary>

After moving data into Tableau, my first step was to begin building maps. A major element that my friend emphasized to me was her wish to be able to see the distribution of healthcare facilities, ideally layered with other relevant pieces of data. From there, I looked at a variety of options, and ultimately decided that to maximize flexibility for users via filtering options while also balancing clarity and ease-of-use, I would build separate dashboards for each major data element (facilities, HPSA designations, health insurance coverage rates, ) along with an overview comparing rural and non-rural areas on these metrics. I also added additional 

</details>

## Link to the Site
Explore [the details and dashboards](https://sites.google.com/view/tnhealthcaremetrics/home) by clicking and hovering to your heart's content!
