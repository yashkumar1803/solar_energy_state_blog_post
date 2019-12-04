# Solar Energy State Blog post
This is a blog post describing some aspects of solar energy based on US states. This is the code block to replicate the findings. Read the blog here: https://medium.com/@yashkumar_73975/three-reasons-that-will-make-you-rethink-solar-energy-in-your-state-2a1289108a88

The auxiliary data and notebooks has been provided here. The main dataset is named seeds_ii_replica.csv, which can be found at https://data.nrel.gov/submissions/81. The sources are from NREL and EIA and based on 2015 data.

# Packages required
1. geopandas
2. matplotlib
3. seaborn
4. numpy
5. pandas
6. camelot (optional)

# Motivation
The idea behind this project is a precursor to a larger endeavor to promote energy and environmental literacy. Stay tuned for more such projects

# Repository files
1. REPLICA Schema.csv: This is an intermediate data dictionary for the REPLICA dataset created from the documentation file
2. SEEDSII REPLICA Documentation (1).pdf: Documentation of all parameters
3. SeriesExport-11-26-2019-22-02-10.csv: Contains monthly solar energy generation (utility-scale and small-scale) at the state level
4. annual_generation_state.xls: Contains broad energy generation data at the state level
5. solar_state_analysis.ipynb: Main python notebook containing all the analysis
6. seeds_ii_replica.csv: main datafile comprising of census tract level data and solar energy attributes (can be found at https://data.nrel.gov/submissions/81)

# CRISP-DM Process
The CRISP-DM process has been utilized in this analysis. The questions are gauged to see how the states differ when it comes to some key factors.

# Business Understanding
The major questions I gained to seek an understanding about were:
1) Is solar energy really affected by the climate of the region?
2) Are the incentives, which are provided at the decentralized (non-federal) level, based on energy-economic factors
3) Is solar energy alleviating any of the concerns with respect to climate change?

# Data Understanding
Here, I have used three different datasets to answer the questions. The dataset majorly used is Solar Energy Evolution and Diffusion Studies (SEEDS) dataset provided by NREL, which has solar energy incentives combined with typical census features for the year 2015. The other two datasets are State Energy Data System (SEDS) dataset. They are used to find state-level annual solar energy production, and its comparison to the total electricity production in the area.

# Prepare Data
This needs to be broken down for each of the three questions as each of them uses different slices of data.

## Question 1
Firstly, I wanted to focus on the climate question. The most obvious elements required to answer that question were climate zones and climate zone description. The main concern was discussing the solar side of it. There were three main contenders to discuss the solar-suitability of the area - 1) suitable number of household counts, 2) suitable number of plane counts and 3) suitable solar-areas. Number of households and plane counts seemed arbitrary because there might be multiple households in the same building. It is not clearly mentioned in the documentation whether there was double counting or not. Plane count also seemed arbitrary because plane sizes differ in different states. The total area seemed like a suitable variable. However, the area component was further divided into different columns by income, ownership and number of families. Aggregating them was possible. However, again the question lay for me, was about the aggregation of climate zones. The options were by household count, tract area, population etc. Tract area seemed to make the most sense. So, a weighted average of the tract climate zones was done by tract area.

#### Missing values: There were only 4 missing values, present for the climate zone values. However, these values were reported in the climate zone description values. So, they were co-opted from the description values.

## Question 2
The second question was related to the incentives at the state-level. There were three incentives given at the state level: capacity-based incentives, production-based incentives and investment-based incentives. When I tried to look at the spread, it was all over the place. The scatter plot of incentives vs energy economic-factors like household income, energy cost or electricity bills were straight lines with no correlations between them. Then, I realized that there were discrete sets of values, with each state having a fixed incentive despite energy-economic factors. Thus, I thought it was better to show straight scatters as boxplots to gain useful information.

#### Missing values: There were no missing values in this case except household median income. There were only 703 (<1%) empty values out of 72,760 values, which were equally distributed amongst all the states. They were neglected.

## Question 3
The third question was related to the impacts that solar energy has made in terms of climate change or global warming. For this, the  
solar energy generated for each of the states was required. Also, every state has energy requirements. Thus, it was important to weight this data by the total electricity generation of the state. This data was found from the SEDS datasets. The total energy dataset was clean. The environmental impact factors were not too many. There was moisture regime, air quality median, air quality 90th percentile, air quality max. Out of this air quality median was chosen, as air quality is an important aspect. It is already getting highly affected in countries like India and China. That's why it was chosen. Also, median was chosen rather than 90th percentile and max as it is very robust to outliers.

#### Missing values: The total energy dataset did not have any missing value. The solar energy dataset had missing values for small-scale solar. However, in many cases, those states had utility-scale solar energy to be very low. It is safe to assume the small-scale residential solar generation would be negligible, especially as a fraction of the total electricity generated. It was considered to be zero.

# Data Modeling
TBC

# Evaluate the Results
The major results of the analysis are:
1. The hottest regions are not necessarily the most suitable for solar energy development
2. States provide uniform economic incentives to each of the census tracts despite wide disparities in energy-economic factors
3. The impact is still not large enough. Despite having the largest share of solar energy, California still ranks the worst in air quality.

The major idea for the report is to encourage energy literacy in the people and thus, the blog post written is from a novitiate point of view and easy to understand. The blog post was kept simple and basic rules were followed to keep the headline and the blog post engaging and useful.

# Acknowledgements
I thank NREL and EIA for their efforts in providing this data to the general public.
