#Data Cleaning Project: World Layoffs Analysis 

This project focuses on the end-to-end data cleaning process of a raw "World Layoffs" dataset using MySQL. The primary goal was to transform a messy dataset into a structured, standardized, and ready-to-analyze format.

🛠 Skills & Tools Used
SQL Concepts: CTEs (Common Table Expressions), Window Functions (ROW_NUMBER), Joins, DDL & DML Commands.

Techniques: Duplicate Removal, Data Standardization, Handling Null Values, Schema Refactoring.

Database: MySQL Workbench.

🚀 The Process
I followed a professional 4-step workflow to clean the data:

1. Creating a Staging Table
To protect the raw data, I created a "staging" table. This ensures that any mistakes made during the cleaning process do not affect the original dataset.

SQL
CREATE TABLE layoffs_staging LIKE layoffs;
INSERT layoffs_staging SELECT * FROM layoffs;
2. Removing Duplicates
I used the ROW_NUMBER() window function partitioned by all columns to identify identical rows.

Created a second staging table (layoffs_staging2) with an extra row_num column.

Deleted all rows where row_num > 1.

3. Data Standardization
This step involved fixing inconsistencies in the text and date columns:

Trimming: Removed unnecessary white spaces from company names.

Grouping: Consolidated various "Crypto" labels (e.g., CryptoCurrency, Crypto) into one single 'Crypto' category.

Fixing Locations/Countries: Cleaned trailing punctuation in country names (e.g., "United States.").

Date Conversion: Converted the date column from TEXT to a proper DATE format using STR_TO_DATE.

4. Handling Null & Blank Values
Identified rows where industry was missing and populated them by joining the table with itself (matching by company).

Removed rows that were completely unusable (where both total_laid_off and percentage_laid_off were NULL).

📈 Final Result
The dataset is now optimized for exploratory data analysis (EDA). The final schema is clean, types are correctly assigned (especially dates), and redundant records are removed.

📂 How to Use
Clone this repository.

Import the layoffs.csv (raw data) into your MySQL instance.

Run the data_cleaning_project.sql script to see the transformation.
