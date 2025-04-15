# Workplace_airplanes
# QCTO - Workplace Module 

### Project Title: Flight Predictions
#### Done By: Kimaya Setty

© ExploreAI 2024

---

## Table of Contents

<a href=#BC> Background Context</a>

<a href=#one>1. Importing Packages</a>

<a href=#two>2. Data Collection and Description</a>

<a href=#three>3. Loading Data </a>

<a href=#four>4. Data Cleaning and Filtering</a>

<a href=#five>5. Exploratory Data Analysis (EDA)</a>

<a href=#six>6. Modeling and Evaluation </a>

<a href=#seven>7. Cross-Validation for Robust Evaluation</a>

<a href=#eight>8. Final Model</a>

<a href=#nine>9. Conclusion and Future Work</a>

---
 <a id="BC"></a>
## **Background Context**
<a href=#cont>Back to Table of Contents</a>

* **Purpose:** Present the project, describe its objectives, and highlight its importance.
* **Details:** Offer background on the problem domain by outlining the main objectives or challenges the project aims to address. Include any relevant context or information that helps clarify the project's purpose and define its overall scope.
---

---
<a href=#two></a>
## **Data Collection and Description**
<a href=#cont>Back to Table of Contents</a>

* **Purpose:** Describe how the data was collected and provide an overview of its characteristics.
* **Details:** Mention sources of the data, the methods used for collection (e.g., APIs, web scraping, datasets from repositories), and a general description of the dataset including size, scope, and types of data available (e.g., numerical, categorical).
---

# Data Collection Details  
- **Source**: The dataset is sourced from Kaggle and can be accessed [here](https://www.kaggle.com/datasets/jinbonnie/airport-information).  


## Dataset Description  
This dataset contains the list of all airport codes, the attributes are identified in data package description. Some of the columns contain attributes identifying airport locations, other codes (IATA, local if exist) that are relevant to identification of an airport.

### Airport 
| Feature Name      | Description  |
|------------------|-------------|
| **ID**    | Internal OurAirports integer identifier for the airport. This will stay persistent, even if the airport code changes.  |
| **Ident**   | The text identifier used in the OurAirports URL. This will be the ICAO code if available. Otherwise, it will be a local airport code (if no conflict), or if nothing else is available, an internally-generated code starting with the ISO2 country code, followed by a dash and a four-digit number. |
| **Type**      | The type of the airport. Allowed values are "closed_airport", "heliport", "large_airport", "medium_airport", "seaplane_base", and "small_airport". See the map legend for a definition of each type.  |
| **Name**    | The official airport name, including "Airport", "Airstrip", etc.  |
| **Latitude deg**  | The airport latitude in decimal degrees (positive for north).  |
| **Longitude deg**    | The airport longitude in decimal degrees (positive for east).  |
| **Elevation ft**       | The airport elevation MSL in feet (not metres).  |
| **Continent**          | The code for the continent where the airport is (primarily) located. Allowed values are "AF" (Africa), "AN" (Antarctica), "AS" (Asia), "EU" (Europe), "NA" (North America), "OC" (Oceania), or "SA" (South America).  |
| **iso_country**       | The two-character ISO 3166:1-alpha2 code for the country where the airport is (primarily) located. A handful of unofficial, non-ISO codes are also in use, such as "XK" for Kosovo. Points to the code column in countries.csv.  |
| **iso_region**      | An alphanumeric code for the high-level administrative subdivision of a country where the airport is primarily located (e.g. province, governorate), prefixed by the ISO2 country code and a hyphen. OurAirports uses ISO 3166:2 codes whenever possible, preferring higher administrative levels, but also includes some custom codes. See the documentation for regions.csv.  |
| **municipality** | The primary municipality that the airport serves (when available). Note that this is not necessarily the municipality where the airport is physically located.  |
| **Scheduled Service**    | "yes" if the airport currently has scheduled airline service; "no" otherwise.  |
| **GPS code** | The code that an aviation GPS database (such as Jeppesen's or Garmin's) would normally use for the airport. This will always be the ICAO code if one exists. Note that, unlike the ident column, this is not guaranteed to be globally unique.  |
| **local_code** | The local country code for the airport, if different from the gps_code and iata_code fields (used mainly for US airports).  |

### Frequency
| Feature Name      | Description  |
|------------------|-------------|
| **ID**    | Internal OurAirports integer identifier for the frequency. This will stay persistent, even if the radio frequency or description changes.  |
| **Airport ref**   |  Internal integer foreign key matching the id column for the associated airport in airports.csv. (airport_ident is a better alternative.) |
| **Airport ident**      | Externally-visible string foreign key matching the ident column for the associated airport in airports.csv.  |
| **Type**    | A code for the frequency type. This isn't (currently) a controlled vocabulary, but probably will be soon. Some common values are "TWR" (tower), "ATF" or "CTAF" (common traffic frequency), "GND" (ground control), "RMP" (ramp control), "ATIS" (automated weather), "RCO" (remote radio outlet), "ARR" (arrivals), "DEP" (departures), "UNICOM" (monitored ground station), and "RDO" (a flight-service station).  |
| **Description**  | A description of the frequency, typically the way a pilot would open a call on it.  |
| **Frequency mhz**    | Radio voice frequency in megahertz. Note that the same frequency may appear multiple times for an airport, serving different functions.  |


## Usage  
This dataset is valuable for:  
- **Exploratory Data Analysis (EDA)**: Understanding airports and their radio frquencies.  
- **Machine Learning**: Developing predictive models to **predict airport types** or **predict radio frquency used by an airport** based on the provided features.  

By leveraging this dataset, financial institutions can gain **data-driven insights** to enhance customer retention strategies and optimize business decisions.

---
<a href=#three></a>
## **Loading Data**
<a href=#cont>Back to Table of Contents</a>

* **Purpose:** Load the data into the notebook for manipulation and analysis.
* **Details:** Present the code used to import the data and display the initial rows, providing an overview of the raw data structure.
---

---
<a href=#four></a>
## **Data Cleaning and Filtering**
<a href=#cont>Back to Table of Contents</a>

* **Purpose:** Prepare the data for analysis by cleaning and filtering.
* **Details:** Outline the steps taken to clean the data, including how missing values were addressed, outliers removed, and errors corrected. If applicable, describe any data reduction techniques used, such as filtering by specific features or criteria.
---

---
<a href=#five></a>
## **Exploratory Data Analysis (EDA)**
<a href=#cont>Back to Table of Contents</a>

* **Purpose:** Explore and visualize the data to uncover patterns, trends, and relationships.
* **Details:** Explore the dataset using both statistical summaries and visual tools such as histograms, box plots, scatter plots, and correlation heatmaps. Highlight and interpret any key patterns, trends, or outliers that emerge from the analysis.
---

---
<a href=#six></a>
## **Modeling and Evaluation**
<a href=#cont>Back to Table of Contents</a>

* **Purpose:** Develop and train predictive or statistical models.
* **Details:** Provide an overview of the selected models, the reasoning behind your feature selection and engineering steps, and explain how each model was trained. Be sure to include code snippets for setting up the models, along with clear explanations of the key parameters used.
---

---
<a href=#seven></a>
## **Cross-Validation for Robust Evaluation**
<a href=#cont>Back to Table of Contents</a>

* **Purpose:** Validate the effectiveness and accuracy of the models.
* **Details:** Outline the metrics used to assess model performance, including accuracy, precision, recall, and F1-score, among others. Also, explain the validation methods applied, such as cross-validation or the train/test split approach.
---

---
<a href=#eight></a>
## **Final Model**
<a href=#cont>Back to Table of Contents</a>

* **Purpose:** Present the final model and its performance.
* **Details:** Identify the top-performing model and elaborate on its setup, performance metrics, and the reasons it was selected over the other models.
---

---
## **Relevent Links**
**Trello:** [trello board](https://trello.com/invite/b/67fca9fc1c658bbdc809d11c/ATTI47f50448cd20977472f025ba2276d8b858041C0F/workplace) 
---
