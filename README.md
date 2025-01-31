TripleTen Sprint 5 Project

Project Summary:
(1) Years below 1993 are not as significant as the rest of the years.  Years 2005 through 2011 are the most competetive.
(2) Display Platforms in descending Platform Sales order (Top 6:  PS2, X360, PS3, Wii, DS, PS)
(3) Based on the top 6 Platforms, it takes between 1 - 4 years to cycle from new to faded for the OLDER year platforms
(4) Based on the top 6 Platforms, it takes between 9 - 11 years to cycle from new to faded for the MORE RECENT years
(5) Since the game cycle trend is between 9 - 11 years, the years to use will be 2012 - 2016 (2017 - 5 [growth cycle midpoint] = 2012)
(6) The top 3 Platforms in this year range (2012 - 2016) are PS4, PS3, X360
(7) The 2 Platforms in decline in this year range (2012 - 2016) are PSP, Wii
(8) Results from PS4 correlation between critic/user scores and sales indicate little or no linear relationship (-0.13 for both calculations)
(9) Two other Platforms produced higher Sales for the same top 20 Game Names (X360 and PS3)
(10)The top 4 sales by genre are:
         Action, Shooter, Role-Playing and Sports
(11) Action and Shooter genres are popular in younger game players, marketing to a younger age group is successful in these genres
(12) The lower sale genres seem to be for 'custom' audiences with specific interests (e.g. Puzzle, Strategy)




Project Planning Section #1: Apply Initial Data Analysis
(A) Open the file and compile observation analysis notes:
    1)  df.info()
            Notes:
                >>  Several columns are missing values
                >>  name, year_of_release, genre, critic_score, user_score, rating
    2)  df.duplicated().sum
            Notes:
                >>  No duplicates noted
    3)  df.describe(...)
            Notes:
                >>  Column year_of_release values are uncharacteristically of type float
                >>  Column user_score has a large frequency of "tbd" values
    4)  df.isna().sum()
            Notes:
                >>  Several columns have a large number of NaN values
                >>  name, year_of_release, genre, critic_score, user_score, rating
    5)  df.unique(...)
            Notes:
                >>  Column critic_score is type "float", but the unique() values all seem to be of type "int"
                >>  Column user_score values are a mixture of "float", NaN and object ("tbd") types
(B) Replace column names 
    1)  make them lowercase (str.lower() )
    2)  df.rename(columns...)
(C) Replace NaN values in "year_of_release", "critic_score", user_score and "rating", replace "TBD" values in 
    "user_score" column by default values completely different from the existing values.  These default values can be used to filter out these rows columns for analysis.
    1)  Replace NaN values in "year_of_release" by 1900
    2)  Replace NaN values in "critic_score" by 888
    3)  Replace all "TBD" values in "user_score" by 999.0
    4)  Replace all NaN values in "user_score" by 888.0
    5)  Replace all NaN values in "rating" by "Unknown"
(D) Convert the data to required types (See #38 in j notebook)
(E) Describe the columns whose data types have been changed and why
    1)  year_of_release from float ==>> int (Date Year is an "int" value)
    2)  critic_score from float ==>> int (running unique() showed how all non-null values do not have any fractions)
    3)  user_score from object ==>> float Numeric values make it possible to make numeric analysis.  The unique 
        replacements preserve and make clear which values were "TBD" and which ones were "NaN"
(F) If necessary, decide how to deal with missing values:
    1)  Explain why missing values have been filled or why they were left blank
        a)  rating (this column has a HUGE number of "NaN". Replace them with "Unknown")
        b)  user_score (replace all "TBD" ==>> 999.0 and fillna() ==>>  888.0  Numeric values make it possible to make 
            numeric analysis.  The unique replacements preserve and make clear which values are "TBD" and which ones are "NaN")
    2)  Explain why the values are missing. Give possible reasons
    3)  Pay attention to the abbreviation TBD (to be determined). Specify intention to handle such cases
    4)  Calculate the total sales (the sum of sales in all regions) for each game and put these values in a separate column

Project Planning Section #2:
   (A) Look at how many games were released in different years. Is the data for every period significant?
   (B) Look at how sales varied from platform to platform. Choose the platforms with the greatest total sales and build a distribution based 
       on data for each year. Find platforms that used to be popular but now have zero sales. How long does it generally take for new 
       platforms to appear and old ones to fade?
   (C) Determine what period you should take data for. To do so, look at your answers to the previous questions. The data should allow you to 
       build a model for 2017
   (D) Work only with the data that you've decided is relevant. Disregard the data for previous years
   (E) Which platforms are leading in sales? Which ones are growing or shrinking? Select several potentially profitable platforms
   (F) Build a box plot for the global sales of all games, broken down by platform. Are the differences in sales significant? What about
       average sales on various platforms? Describe your findings.
   (G) Take a look at how user and professional reviews affect sales for one popular platform (you choose). Build a scatter plot and 
       calculate the correlation between reviews and sales. Draw conclusions
   (H) Keeping your conclusions in mind, compare the sales of the same games on other platforms
   (I) Take a look at the general distribution of games by genre. What can we say about the most profitable genres? Can you generalize about 
       genres with high and low sales?

Project Planning Section #3:
   (A) For each region (NA, EU, JP), determine:
       1)  The top five platforms. Describe variations in their market shares from region to region
       2)  The top five genres. Explain the difference
       3)  Do ESRB ratings affect sales in individual regions?

Project Planning Section #4:
   (A) Test the following hypotheses:
       1)  Average user ratings of the Xbox One and PC platforms are the same. 
       2)  Average user ratings for the Action and Sports genres are different.
       3)  Set the alpha threshold value yourself.
           Explain:
           a)  How you formulated the null and alternative hypotheses 
           b)  What significance level you chose to test the hypotheses, and why

Project Planning Section #5:
   (A) Write a general conclusion
 