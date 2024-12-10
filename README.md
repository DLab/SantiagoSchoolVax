# SantiagoSchoolVax

## Documentation for Code

## Overview

This Python script analyzes the correlation between socioeconomic status (SES) indices and vaccination coverage against COVID-19 among school-aged children in Santiago, Chile, as published in Scientific Reports (in review). The script leverages multiple datasets, including vaccination data, school metadata, and socioeconomic indicators, to explore relationships using geospatial and statistical methods.

## Modules Used

	•	Pandas: Data manipulation and analysis.
	•	Pathlib: File system path handling.
	•	Datetime: Date and time operations.
	•	Seaborn: Statistical data visualization.
	•	Matplotlib: Plotting library for visualizations.
	•	Scipy: Statistical analysis.
	•	Geopandas: Geospatial data analysis.
	•	Mapclassify: Classification schemes for choropleth maps.

## Data Inputs

	1.	Vaccination Data:
	•	Location: JSON files (e.g., vaccines_data/vacunacionescolar.mineduc.cl_*)
	•	Data includes school-level vaccination percentages for various grade levels.
	2.	Metadata from Ministry of Education (MINEDUC):
	•	Location: inputs/mineduc_data/20210927_Directorio_Oficial_EE_2021_20210430_WEB.csv
	•	Contains school attributes such as latitude, longitude, dependency codes, and rurality.
	3.	Socioeconomic Indicators:
	•	Location: inputs/cut_idc_pvrty.csv
	•	Includes poverty rates, composite development indices (CDI), and SPI indicators.
	4.	Geospatial Boundaries:
	•	Location: inputs/Comunas/comunas.shp
	•	Shapefile of administrative boundaries for Santiago, Chile.

## Key Variables and Functions

### Mappings

	•	COD_DEPE2_tr: Translates school dependency codes into descriptive labels.
	•	RURAL_RBD_tr: Maps rurality indicator values to Urban or Rural.
	•	ORI_RELIGIOSA_tr: Translates school religious orientation codes to descriptive labels.

### Functions

	1.	download_json_vac:
	•	Automates downloading JSON files from the vaccination school website.
	•	Command-line tool: wget.
	2.	clip_area_geodataframe:
	•	Clips geospatial data to a specific bounding box.
	•	Handles ill-defined polygon intersections gracefully.
	3.	corrfunc and spearmanrfunc:
	•	Annotates scatterplots with correlation coefficients and p-values for relationships between variables.

## Workflow

	1.	Data Loading and Preprocessing:
	•	Loads vaccination data from JSON files.
	•	Reads and merges socioeconomic and school metadata.
	•	Filters data for relevant grade levels and Metropolitan Santiago.
	2.	Mapping Geospatial Data:
	•	Loads administrative boundaries for Santiago.
	•	Clips data to the bounding box for the study region.
	3.	Statistical Analysis:
	•	Calculates Pearson and Spearman correlations between vaccination coverage and SES indicators.
	•	Implements Fisher-Jenks classification for bivariate choropleth maps.
	4.	Visualization:
	•	Scatterplots: Displays relationships between SES indicators and vaccination coverage.
	•	Bivariate Maps: Combines SES and vaccination data into color-coded maps.
	5.	Gini Index Calculation:
	•	Computes Gini coefficients for vaccination coverage inequality across grade levels.

## Outputs

	1.	Figures:
	•	Scatterplots and bivariate maps showing relationships between SES indices and vaccination coverage.
	•	Geospatial visualizations for different school dependency types.
	2.	Dataframes:
	•	Merged datasets for further analysis.
	•	Ranked communes based on SES indices.

## How to Run the Code

	1.	Set Up Environment:
	•	Install required Python libraries: pandas, geopandas, seaborn, matplotlib, scipy, mapclassify.
	•	Ensure all input datasets are correctly placed in their respective directories.
	2.	Execute the Script:
	•	Run the script in Python or Jupyter Notebook.
	•	Outputs are saved to specified directories or displayed in the notebook.

## Notes

	•	Customizable Parameters:
	•	Change json_dir, cursos, and bounding box (bbox2) to adapt to other datasets or regions.
	•	Modify vac_bins and spi_bins for different classification schemes.
	•	Dependencies:
	•	Ensure geospatial data uses the same coordinate reference system (CRS) as the study area.
	•	Error Handling:
	•	The script includes checks for missing data and coerces errors where possible (e.g., invalid numerical conversion).
