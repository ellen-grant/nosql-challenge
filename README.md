# UK Food Hygiene Database Analysis

## Project Overview
This project involves analyzing the UK Food Standards Agency's food hygiene ratings dataset. The
dataset includes hygiene inspection results for various food establishments across the United
Kingdom, along with detailed information about their location, rating values, and other inspection
scores. The analysis is conducted to assist the magazine Eat Safe, Love in selecting restaurants for
review and further articles

### Key Objectives:
1. Database Setup and Modifications:
   - Load the dataset into MongoDB and perform initial database setup, including cleaning and
transforming certain fields for better analysis.
  - Add new establishments and update existing ones as per business requirements.
2. Exploratory Data Analysis:
  - Answer specific questions posed by the magazine's editors to provide actionable insights.
  - Analyze hygiene scores, rating values, and geographical distribution of establishments.
3. Aggregation and Queries:
  - Use MongoDB aggregation pipeline to gather insights on hygiene scores, location-based
analysis, and more.

## Project Structure
Files:
  - NoSQL_setup_starter.ipynb: Jupyter notebook for the initial database setup, importing data into
MongoDB, and performing modifications like adding new establishments.
  - NoSQL_analysis_starter.ipynb: Jupyter notebook for performing exploratory data analysis based
on queries defined by the magazine editors.
  - establishments.json: The dataset containing food establishments and their hygiene ratings.
  - README.md: Documentation of the project.

## Steps Performed:
1. Database Setup:
    - Import the establishments.json file into a MongoDB collection named establishments.
    - Perform initial checks on the database (e.g., listing collections, ensuring data integrity).
    - Modify certain fields, such as updating BusinessTypeID for a new restaurant, converting string
fields to numeric where appropriate.
2. Analysis Tasks:
    - Hygiene Score Queries: Analyze and filter establishments based on specific hygiene scores.
    - Location-Based Queries: Use geocode data to analyze establishments within a specific location
range.
    - Aggregation Queries: Use MongoDB's aggregation pipeline to group data by Local Authority and
summarize hygiene-related results.

## Analysis Results
### Key Findings:
1. Establishments with Hygiene Score of 20: Identified a subset of establishments with a hygiene
score of 20, which is of concern since higher values indicate worse hygiene practices.
2. Highly Rated Establishments in London: Found that a number of establishments in the London
area have a rating value of 4 or above, making them prime candidates for feature articles.
3. Top 5 Establishments near Penang Flavours: Analyzed establishments near the new restaurant
"Penang Flavours" and identified the top 5 with a RatingValue of 5, sorted by their hygiene scores.
These nearby establishments are well-maintained in terms of hygiene.
4. Hygiene Scores by Local Authority: Aggregated establishments by Local Authority and identified
areas with the most establishments having a hygiene score of 0. The top areas are places where
the magazine may want to investigate for potential issues.

## Limitations
1. Data Quality:
 - Some RatingValue fields were stored as strings rather than integers, which required cleaning and
conversion. The dataset also included non-numeric values like "Pass" or "Awaiting Inspection,"
which we had to handle as null values.
2. Limited Location Precision:
 - Geocoding data (latitude and longitude) had only a limited degree of precision. In certain cases,
this might impact the accuracy of "nearest establishment" calculations.
3. Non-Numeric Scores:
 - Fields such as scores.Hygiene, scores.Structural, and scores.ConfidenceInManagement reflect
inverse values (i.e., higher numbers indicate worse conditions), which may cause confusion if not
handled carefully in the analysis.
4. Partial Data:
 - The dataset represents a snapshot in time and may not include recent updates or changes in
food hygiene ratings, especially for new establishments.

## Conclusion and Recommendations
This project provided key insights into food hygiene standards across various regions in the UK. By
identifying establishments with the best and worst hygiene scores, we have a clearer understanding
of where Eat Safe, Love can focus its future articles. Specifically, the analysis around highly rated
restaurants in the London area and problem spots with low hygiene scores provides actionable
information for the magazine's editorial team.

## How to Run
### Prerequisites:
- MongoDB: Ensure MongoDB is installed and running on your local machine.
- Python: Requires Python 3.x and the following libraries:
- pymongo
- pandas
- pprint
### Steps:
1. Clone the repository or download the necessary files.
2. Use mongoimport to import the establishments.json dataset into MongoDB:
 mongoimport --db uk_food --collection establishments --file establishments.json --jsonArray
3. Open the Jupyter notebooks (NoSQL_setup_starter.ipynb and NoSQL_analysis_starter.ipynb) to
perform database setup and data analysis.

## References
UK Food Standards Agency (https://www.food.gov.uk/) (2022). UK food hygiene rating data API. (https://ratings.food.gov.uk/open-data/en-GB). Contains public sector information licensed under the Open Government Licence v3.0(https://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/).
Accessed Sept 9, 2022 and Sept 12, 2022 with the establishment settings as follows: longitude=51.5072, latitude=-0.1276, maxdistancelimit=4567, pagesize=10000, sortoptionkey=distance, pagenumber=(1,2,3,4,5,6,7,8).
