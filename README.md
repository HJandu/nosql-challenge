# <p align="center"> <ins>NoSQL-Challenge</ins>

## <ins>Background</ins>
The UK Food Standards Agency evaluates various establishments across the United Kingdom, and gives them a food hygiene rating. I've been contracted by the editors of a food magazine, Eat Safe, Love, to evaluate some of the ratings data in order to help their journalists and food critics decide where to focus future articles.

## <ins>Part 1: Database and Jupyter Notebook Set Up</ins>

Using the `NoSQL_setup_starter.ipynb` notebook, I Imported the data provided in the establishments.json file from my Terminal. The database is named uk_food and the collection is called establishments. 
The following text was used to import the data from terminal. 

`mongoimport --type json -d uk_food -c establishments --drop --jsonArray establishments.json`

Within my notebook, I had imported the libraries I needed: PyMongo and Pretty Print (pprint). I then created an instance of the Mongo Client and confirmed that I had created the database and loaded the data properly.

## <ins>Part 2: Update the Database</ins>

The magazine editors have some requested modifications for the database before I could perform any queries or analysis for them. So I made the following changes to the establishments collection:

- Added information to the database about an exciting new halal restaurant that just opened in Greenwich, but hadn't been rated yet.
- Found the `BusinessTypeID` for "Restaurant/Cafe/Canteen" and returned only the `BusinessTypeID` and `BusinessType` fields.
- Updated the new restaurant with the `BusinessTypeID` I found.
- Checked how many documents contain the Dover Local Authority. 
- Removed any establishments within the Dover Local Authority from the database, and checked the number of documents to ensure they were deleted.
- Used `update_many` to convert latitude and longitude to decimal numbers, because some of the number values were stored as strings, when they should have been stored as numbers. 

## <ins>Part 3: Exploratory Analysis</ins>

RatingValue refers to the overall rating decided by the Food Authority and ranges from 1-5. The higher the value, the better the rating. Note: This field also includes non-numeric values such as 'Pass', where 'Pass' means that the establishment passed their inspection but isn't given a number rating.
The scores for Hygiene, Structural, and ConfidenceInManagement work is in reverse. This means, the higher the value, the worse the establishment is in these areas.

Using the `NoSQL_analysis_starter.ipynb` for this section of the challenge, I was able to explore the dataset, so I could provide them to the magazine editors.


- I used `count_documents` to display the number of documents contained in the result.

- I was able to display the first document in the results using pprint.

- I converted the result to a Pandas DataFrame, printed the number of rows in the DataFrame, and displayed the first 10 rows.

- I was able to findout which establishments have a hygiene score equal to 20.

- I was able to findout which establishments in London have a RatingValue greater than or equal to 4.

- I was able to findout what are the top 5 establishments with a RatingValue of '5', sorted by lowest hygiene score, nearest to the new restaurant added, "Penang Flavours".
- I was able to findout how many establishments in each Local Authority area have a hygiene score of 0. I then sorted the results from highest to lowest, and printed out the top ten local authority areas.


The first 5 rows of the resulting DataFrame can be see below:

![Screen Shot 2023-01-27 at 01 18 21](https://user-images.githubusercontent.com/116304118/214987457-2cb2ceb4-2d69-45e7-afcb-2b19206e2562.png)

