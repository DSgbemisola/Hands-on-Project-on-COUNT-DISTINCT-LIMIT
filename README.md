# Hands-on project on using COUNT-DISTINCT-LIMIT Expressions in SQL

This is a hands-on project to demostrate skills in writing COUNT, DISTINCT AND LIMIT expressions with SELECT statements. 

# Objectives

The objective this project are to:

1. Retrieve the number of rows that match a query criteria
2. Remove duplicate values from a result set and return the unique values
3. Restrict the number of rows retrieved from a table

# Highlights

COUNT, DISTINCT AND LIMIT expressions are used with SELECT statements. 

COUNT is an aggregate function that retrieves the number of rows that matches the query criteria. 
DISTINCT is used to remove duplicate values from a specified result set and only return the unique values. 
LIMIT is used for restricting the number of rows retrieved from the table.

# Software Used in this Project

In this project, I used PgAdmin 4 (PostgreSQL 15)

# Database Used in this Lab

The database used in this project comes from the following dataset source: Film Locations in San Francisco under a PDDL: Public Domain Dedication and License.
Dataset is downloadable here: https://drive.google.com/file/d/1xzX-gZTRZBT3XHwSJ1L34DbnszwQzdxC/view?usp=sharing

# Project Phases

The project was conducted in Four (4) phases as detailed below:

# Phase 1: Creating the SanFranciscoFilmLocations Database and filmlocations Table in PgAdmin

The first phase of the project involved creating our SanFranciscoFilmLocations Database and filmlocations Table in PgAdmin, followed by loading the FilmLocations CSV file. I achieved this by going through the following steps:

# Step 1: Creating a Database

1. I opened PgAdmin on my local computer and connected to my PostgreSQL server,
2. Right-clicked on the "Databases" node in the Browser panel on the left-hand side,
3. Selected "Create" > "Database",
4. In the "New Database" window:
   a. I entered the name of my database, "SanFranciscoFilmLocations", 
   b. Selected the owner (usually your PostgreSQL username, e.g., ELITEBOOK 840),
   C. Clicked "Save" to create the database.

# Step 2: Creating a Table

1. I navigated to my new database named "SanFranciscoFilmLocations":
   a. Expanded the "Databases" node,
   b. Expanded the "SanFranciscoFilmLocations" node,
2. Right-clicked on the "Tables" node under my new database,
3. Selected "Create" > "Table",
4. In the "Create - Table" window:
   a. I entered the name of my table, "filmlocations",
   b. Navigated to the "Columns" tab,
5. Added columns to your table:
   a. Clicked the "+" button to add a new column.
   b. For each column, I entered the name and selected the data type (e.g., VARCHAR, INTEGER)
   c. Repeated for all columns as defined below:

![image](https://github.com/DSgbemisola/Hands-on-Lab-Basics-of-SQL-SELECT-Statement/assets/116846702/23551016-34a7-40d7-b53b-eb3096b7f7e9)

6. Clicked "Save" to create the table.

# Step 3: Load Data from CSV Using PgAdmin Import/Export Feature

1. I Right-clicked on the "filmlocations" table in PgAdmin.
2. Selected "Import/Export Data".
3. In the "Import/Export Data" dialog:
   a. Selected "Import".
   b. Chose the file path to my CSV file (C:\Users\ELITEBOOK 840\Documents\FilmLocations.csv).
   c. Set the Format to CSV.
   d. Ensured Header is checked since my CSV file includes headers.
   e. Clicked "Columns" tab and verify the table columns.
4. Clicked "OK" to import the data.

# Phase 2: Exploring the Database

After successfully loading my data, I first explored the SanFranciscoFilmLocations database.
   1. I right-clicked on the "FilmLocations" table and 
   2. Selected "View/Edit Data" > "First 100 Rows".

See screenshot of the resultset:

![image](https://github.com/DSgbemisola/Hands-on-Lab-Basics-of-SQL-SELECT-Statement/assets/116846702/333a5eb0-df5d-4aa2-b7f8-4d826a7781bb)

# Phase 3: Using COUNT in queries and answering questions with the COUNT expression.

# Task 1: How many number of records or rows are there in the “filmlocations” table.

Solution: I retrieved the number of rows from the “filmlocations” table using the SQL statement below:
        
         SELECT COUNT (*) as total_number_of_records FROM filmlocations;

![image](https://github.com/DSgbemisola/Hands-on-Project-on-COUNT-DISTINCT-LIMIT/assets/116846702/a315e938-b9d6-4c79-a0f4-8be3b210b055)

# Task 2: What is the number of locations of the films which are written by James Cameron.

Solution: I retrieved the number of filming locations that are written by James Cameron using the SQL statement below:

        SELECT COUNT(locations) as exclusive_number_of_locations 
        FROM filmlocations
        WHERE writer = 'James Cameron';

![image](https://github.com/DSgbemisola/Hands-on-Project-on-COUNT-DISTINCT-LIMIT/assets/116846702/ea1bbdc4-0847-4a01-b256-92200977d0af)

# Task 3: What is the number of locations of the films which are directed by Woody Allen.

Solution: I retrieved the number of locations of the films which are directed by Woody Allen using the SQL statement below:

        SELECT COUNT(locations) as exclusive_number_of_locations 
        FROM filmlocations
        WHERE director = 'Woody Allen';

![image](https://github.com/DSgbemisola/Hands-on-Project-on-COUNT-DISTINCT-LIMIT/assets/116846702/b46cfcd5-d12a-472d-a43b-e2b61c647c3b)

# Task 4: How many films were shot at Russian Hill.

Solution: I retrieved the number of films shot at Russian Hill using the SQL statement below:

        SELECT COUNT(*) as exclusive_number_of_locations 
        FROM filmlocations
        WHERE director = 'Russian Hill';

![image](https://github.com/DSgbemisola/Hands-on-Project-on-COUNT-DISTINCT-LIMIT/assets/116846702/5450333a-be02-4fc4-9ec3-9fe223207e7f)

# Task 5: How many films were released in years older than 1950 from the “FilmLocations” table.

Solution: I retrieved the number of films released in years older than 1950 from the filmlocations table using the SQL statement below:

        SELECT COUNT(*) as films_released_in_1950_upwards
        FROM filmlocations
        WHERE releasedyear < 1950;

![image](https://github.com/DSgbemisola/Hands-on-Project-on-COUNT-DISTINCT-LIMIT/assets/116846702/9a4733a2-a070-46d5-b719-51334ff8ec9e)

# Task 6: Retrieve the title of all films in the table without any duplicate titles.

Solution: I retrieved the name of all films without any repeated titles using the SQL statement below:
        
        SELECT DISTINCT title as film_title FROM filmlocations

![image](https://github.com/DSgbemisola/Hands-on-Project-on-COUNT-DISTINCT-LIMIT/assets/116846702/20b81f25-d341-4d89-a85f-8adcca6332d2)

# Task 7: Retrieve the count of release years of the films produced by Warner Bros. Pictures without duplicating release years.

Solution: I retrieved the number of release years of the films distinctly, produced by Warner Bros. Pictures using the SQL statement below:

        SELECT COUNT(DISTINCT releaseyear) as number_of_distinct_films 
        FROM filmlocations
        WHERE productioncompany = 'Warner Bros. Pictures';

![image](https://github.com/DSgbemisola/Hands-on-Project-on-COUNT-DISTINCT-LIMIT/assets/116846702/42c815f2-155c-4279-b22a-ce7d402693a1)

# Task 8: Retrieve the name of all unique films released in the 21st century and onwards, along with their release years.

Solution: I retrieved the name of all unique films released in the 21st century and onwards, along with their release years using the SQL statement below:

        SELECT DISTINCT title as film_title, releaseyear as year_of_release
        FROM filmlocations
        WHERE releaseyear >= 2001;

![image](https://github.com/DSgbemisola/Hands-on-Project-on-COUNT-DISTINCT-LIMIT/assets/116846702/e5ac83fb-c03c-4561-8651-b39302d8a3e2)

# Task 10: Retrieve the names of all the directors and their distinct films shot at City Hall.

Solution: I retrieve the names of all the directors and their distinct films shot at City Hall using the SQL statement below:

        SELECT title as film_title, DISTINCT director as director_name
        FROM filmlocations
        WHERE locations = 'City Hall';

![image](https://github.com/DSgbemisola/Hands-on-Project-on-COUNT-DISTINCT-LIMIT/assets/116846702/25ea7a81-4e26-4962-8ead-33f3ef4db756)

# Task 9: Retrieve the number of distributors distinctly who distributed films acted by Clint Eastwood as 1st actor.

Solution: I retrieved the number of distinct distributors who distributed films acted by Clint Eastwood as 1st actor using the SQL statement below:

        SELECT COUNT(DISTINCT distributor) as number_of_distinct_distributor
        FROM filmlocations
        WHERE actor1 = 'Clint Eastwood';

![image](https://github.com/DSgbemisola/Hands-on-Project-on-COUNT-DISTINCT-LIMIT/assets/116846702/7415b766-7852-4e75-bdd9-e93928822829)

# Task 10: Retrieve the first 25 rows from the “FilmLocations” table.

Solution: I retrieved the first 25 rows from the “FilmLocations” table using the SQL statement below:

        SELECT *
        FROM filmlocations
        LIMIT 25;

![image](https://github.com/DSgbemisola/Hands-on-Project-on-COUNT-DISTINCT-LIMIT/assets/116846702/db892cca-0617-4964-ad27-49ea4f743881)

# Task 11: Retrieve the first 15 rows from the “FilmLocations” table starting from row 11.

Solution: I retrieved the first 15 rows from the “FilmLocations” table starting from row 11 using the SQL statement below:

        SELECT *
        FROM filmlocations
        LIMIT 15 OFFSET 10;

![image](https://github.com/DSgbemisola/Hands-on-Project-on-COUNT-DISTINCT-LIMIT/assets/116846702/aa29242c-e0f8-4580-9954-162a31e3737f)

# Task 12: Retrieve the name of first 50 films distinctly.

Solution: I retrieved the name of distinct first 50 films using the SQL statement below:

        SELECT DISTINCT title as film_title
        FROM filmlocations
        LIMIT 50;

![image](https://github.com/DSgbemisola/Hands-on-Project-on-COUNT-DISTINCT-LIMIT/assets/116846702/edf57bf8-6fb9-43c5-a1af-3e27dbcc5596)

# Task 13: Retrieve first 10 film names distinctly released in 2015.

Solution: I retrieved first 10 film names distinctly released in 2015 using the SQL statement below:
     
        SELECT DISTINCT title as film_title
        FROM filmlocations
        WHERE releaseyear = 2015
        LIMIT 10;

![image](https://github.com/DSgbemisola/Hands-on-Project-on-COUNT-DISTINCT-LIMIT/assets/116846702/5fa40289-4726-4a7b-859e-08ecf8fe510f)

# Task 14: Retrieve the next 3 film names distinctly after first 5 films released in 2015.

Solution: I retrieved first 10  distinct film names released in 2015 using the SQL statement below:

        SELECT DISTINCT title as film_title
        FROM filmlocations
        WHERE releaseyear = 2015
        LIMIT 3 OFFSET 5;

![image](https://github.com/DSgbemisola/Hands-on-Project-on-COUNT-DISTINCT-LIMIT/assets/116846702/32b5cb83-a217-4407-8b1e-7290aeda19f6)




      



    
