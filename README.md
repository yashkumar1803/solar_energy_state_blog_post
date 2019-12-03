# Solar Energy State Blog post
Written a blog post on various aspects of solar energy based on US states. This is the code block to replicate the findings. Read the blog here: https://medium.com/@yashkumar_73975/three-reasons-that-will-make-you-rethink-solar-energy-in-your-state-2a1289108a88

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

# Results of the analysis
The major results of the analysis are:
1. The hottest regions are not the most suitable for solar energy development
2. States provide uniform economic incentives to each of the census tracts despite wide disparities in energy-economic factors
3. The impact is still not large enough. Despite having the largest share of solar energy, California still ranks the worst in air quality.

# Acknowledgements
I thank NREL and EIA for their efforts in providing this data to the general public.
