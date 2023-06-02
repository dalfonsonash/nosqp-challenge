## nosqp-challenge
# Instructions
The UK Food Standards Agency evaluates various establishments across the United Kingdom, and gives them a food hygiene rating. You've been contracted by the editors of a food magazine, Eat Safe, Love, to evaluate some of the ratings data in order to help their journalists and food critics decide where to focus future articles.

# Part 1: Data and Jupyter Notebook Set up
Use NoSQL_setup_starter.ipynb file.
1. Import data from establishments.json file from gitbash terminal. Name the database -d uk_food and the collection -c establishments.  
Copy the text used to import data from your gitbash terminal to a markdown cell in jupyter notebook.
2.  Within the notebook, import the libraries: PyMongo and Pretty Print(pprint).
3.  Create an instance of the Mongo Client.
4.  Confirm that you created the database and loaded the data properly:
  List the databases you have in MongoDB. Confirm that uk_food is listed.
  List the collection(s) in the database to ensure that establishments is there.
  Find and display one document in the establishments collection using find_one and display with pprint.
5. Assign the establishments collection to a variable to prepare the collection for use.

# Part 2: Update the Database
Use NoSQL_setup_starter.ipynb file.
Make the following changes to the 'establishments' collection:
1. Add the following information to the database:
  {
    "BusinessName":"Penang Flavours",
    "BusinessType":"Restaurant/Cafe/Canteen",
    "BusinessTypeID":"",
    "AddressLine1":"Penang Flavours",
    "AddressLine2":"146A Plumstead Rd",
    "AddressLine3":"London",
    "AddressLine4":"",
    "PostCode":"SE18 7DY",
    "Phone":"",
    "LocalAuthorityCode":"511",
    "LocalAuthorityName":"Greenwich",
    "LocalAuthorityWebSite":"http://www.royalgreenwich.gov.uk",
    "LocalAuthorityEmailAddress":"health@royalgreenwich.gov.uk",
    "scores":{
        "Hygiene":"",
        "Structural":"",
        "ConfidenceInManagement":""
    },
    "SchemeType":"FHRS",
    "geocode":{
        "longitude":"0.08384000",
        "latitude":"51.49014200"
    },
    "RightToReply":"",
    "Distance":4623.9723280747176,
    "NewRatingPending":True
}

2. Find the Business TypeID for "Restaurant/Cafe/Canteen" and return only the 'BusinessTypeID' and 'BusinessType' fields.
3. Update the new restaurant with the 'BusinessTypeID you found.
4. Find how many documnets contain the Dover Local Authority.  Then, remove any establishments within the Dover Local Authority from the database, and check the number of documents to verify deletion.
5. Some of the number values are stored as strings, but need conversion to numbers.
   Use 'update_many' to convert 'latitude' and 'longitude' to decimal numbers.
   Use update_many' to convert 'RatingValue' to integer.
   
# Exploratory Analysis:
Use NoSQL_analysis_starter.ipynb for this section of the challenge.
RatingValue refers to the overall rating decided by the Food Authority and ranges from 1-5. The higher the value, the better the rating.
Note: This field also includes non-numeric values such as 'Pass', where 'Pass' means that the establishment passed their inspection but isn't given a number rating. We will coerce non-numeric values to nulls during the database setup before converting ratings to integers.
The scores for Hygiene, Structural, and ConfidenceInManagement work in reverse. This means, the higher the value, the worse the establishment is in these areas.
Use count_documents to display the number of documents contained in the result.

Display the first document in the results using pprint.

Convert the result to a Pandas DataFrame, print the number of rows in the DataFrame, and display the first 10 rows.

Which establishments have a hygiene score equal to 20?

Which establishments in London have a RatingValue greater than or equal to 4?

Hint: The London Local Authority has a longer name than "London" so you will need to use $regex as part of your search.

What are the top 5 establishments with a RatingValue of 5, sorted by lowest hygiene score, nearest to the new restaurant added, "Penang Flavours"?

Hint: You will need to compare the geocode to find the nearest locations. Search within 0.01 degree on either side of the latitude and longitude.

How many establishments in each Local Authority area have a hygiene score of 0? Sort the results from highest to lowest, and print out the top ten local authority areas.

Hint: You will need to use the aggregation method to answer this.

The first 5 rows of your resulting DataFrame should look something like this:

![image](https://github.com/dalfonsonash/nosqp-challenge/assets/126922261/19d3eb51-b610-4e52-83a3-ad1a7fb758dd)


