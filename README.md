# DATA 512 A2<br>
Madalyn Li<br>
Fall 2021

# Goal
The goal of this project is to uncover details about biases within English Wikipedia articles about political figures from various countries. In particular, we look at two measures to gauge our understanding of biases: proportion of articles per population and proportion of high quality articles both grouped by country and geographic region. 
The code and steps available to reproduce the analysis is located within the jupyter notebook in this repository named *hcds-a2-bias*.

# Data Sources
This project uses data from three different sources:
1. [Politicians by Country from the English-language Wikipedia](https://figshare.com/articles/dataset/Untitled_Item/5513449)<br>
This file is available to download for free under a [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) license. The file can also be found in the repository within the Data Sources folder and is titled *page_data.csv*. The data includes information on most English Wikipedia articles that fall in the category: “Politicians by nationality”. The file contains three columns with their descriptions listed below:

| Column | Description |
| --- | --- |
| **page** | Contains the page title of the article |
| **country** | Contains the country name extracted from the category |
| **rev_id** | Contains the revision ID of the last edit made to the page |

2. [World Population from PRB](https://www.prb.org/international/indicator/population/table/) <br>
This file can be found in the repository within the Data Sources folder and is titled *WPDS_2020_data.csv*. The data includes information on the estimated world population in mid-2020. The file contains 6 columns with their descriptions listed below:

| Column | Description |
| --- | --- |
| **FIPS** | Contains the abbreviated country/sub-region name |
| **Name** | Contains the name of the country/sub-region |
| **Type** | Contains the category of Name (i.e country or sub-region) |
| **Timeframe** | Contains the year that the data was collected |
| **Data(M)** | Contains the population in millions |
| **Population** | Contains the total population |

3. [ORES REST API](https://ores.wikimedia.org/v3/#!/scoring/get_v3_scores_context_revid_model)<br>
The data file from the ORES API query can be found in the repository within the Data Sources folder and is titled *ores_api_scores.csv*. The data file includes information on the predicted article quality scores corresponding to the article revision ids in the Politicians by Country English-language Wikipedia data set. A description of the ranked scores are listed in the table below from best to worst:

| Score | Description |
| --- | --- |
| FA | Featured article |
| GA | Good article |
| B | B-class article |
| C | C-class article |
| Start | Start-class article |
| Stub | Stub-class article |

It is important to note that not all articles in the Politicians by Country English-language Wikipedia dataset were found within the ORES API. Thus, we have included these article revision ids in a separate csv file that is located in the Additional Data folder. This file is named: *ores_api_no_score.csv*. 

# Clean Data File

The final clean data file is located in the Clean Data folder within the repository; the file is titled *wp_wpds_politicians_by_country.csv*. The table below includes a list of all the fields in this cleaned dataset along with a short description of each. 

| Column | Description |
| --- | --- |
| revision_id | Contains the revision ID of the last edit made to the Wikipedia page article |
| article_quality_est | Contains the predicted article quality score |
| article_name | Contains the page title of the article |
| country | Contains the country based on the Wikipedia article category: “politician by nationality” |
| geographic region | Contains the geographic region of the country listed |
| population | Contains the total population |

When merging the three datasets together, there were inevitably some countries that did not match with the other table. For the instances where no matches were found on either data set, the values were saved within a file in the Additional Data folder located in the repository. The file is named: *wp_wpds_countries-no_match.csv*.

# File Descriptions

Below is a table of the descriptions for each file within this repository. They are listed in a general order to follow when reproducing the analysis:

| File Name | Description |
| --- | --- |
|ores_api_no_score.csv | **Not needed for analysis**: This file contains all the article revision ids that did not produce a predicted score through the ORES API |
|wp_wpds_countries-no_match.csv | **Not needed for analysis**: This file contains all data for the countries that did not match to both the Wikipedia article dataset and the world population dataset |
|page_data.csv | This file contains information on Politicians by Country from the English-language Wikipedia |
|WPDS_2020_data.csv | This file contains estimated world population  by country in mid-2020 |
|ores_api_scores.csv | This file contains the article revision ids with their corresponding predicted scores obtained from the ORES API |
|wp_wpds_politicians_by_country.csv | This file contains all country matches between the Wikipedia article dataset and the world population dataset. This is our finalized clean dataset used for analysis |
|hcds-a2-bias.ipynb | This file contains a Jupiter notebook containing all code and documentation for the analysis of this project |

# Resources
1. [Politicians by Country from the English-language Wikipedia](https://figshare.com/articles/dataset/Untitled_Item/5513449)
2. [World Population from PRB](https://www.prb.org/international/indicator/population/table/)
3. [ORES REST API](https://ores.wikimedia.org/v3/#!/scoring/get_v3_scores_context_revid_model)

# Additional Notes

In the Politicians by Country from the English-language Wikipedia dataset, we removed page titles starting with “Template:” to not include in our analysis since these are not considered articles. 



