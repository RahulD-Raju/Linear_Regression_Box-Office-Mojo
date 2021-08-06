# A More Scientific Approach to Profitable Movie Making
Prepared by Rahul D. Raju

# Abstract
In the 21st century, institutions and industries across the globe have embraced the use of big-data in their
decision making processes. Each of these organizations and industries face unique challenges which in turn
affects the use and efficacy of this data. One industry with particularly interesting challenges is film making.
Hollywood faces the dual task of not only making “good” movies but ensuring they are profitable as well.
This can be somewhat difficult as the two factors are not always correlated. Also, the notion as to what
makes a “good movie” in the pre-production phase can be highly subjective. As most if not all major studios
now belong to publicly listed media conglomerates, a significant emphasis is now being placed on the
profitably component of this equation. Particularly with the stock market at all time highs, movie industry
stocks could be susceptible to anything that diminishes the bottom line. Thus studios must explore every
possible avenue in ensuring that the spectacular losses of the past are not repeated or at the very least
minimized.  One avenue worth exploration is the use of statistical based algorithms such Linear Regression.
The aim is to make the choice of which movies to produce as least subjective as possible 

# Data
Nearly 15000 movies were scraped from the Box Office Mojo website, with supplemental information scraped 
from imdb.com.  12 of the features are categorical, with 3 being quantitative.

Target Variable:  World Wide Box Office Gross
List of Features:  
* Budget                    
* Distributor
* Rating                  
* Producer
* Run Time            
* Writer
* Genre              
* Actors x 3
* Season Released     
* Director

# Methodology/Algorithms

Web Scrapping:  Beautiful soup was employed to loop through the main tables of Box-Office-Mojo, and then looped through each
movie individually.  



Linear Regression Modeling

- Ran a pairplot to of quantitative variables to determine type of relationships between target and feature
- Performed a baseline regression of only quantitative variables
- Transformed 'budget' feature into a polynomial in order to  capture curvelinear relationship with target
- Attempted to regress against the log transformation of the target, resulted in lower R^2
- Converted all categorical columns to dummy variables and re-ran baseline regression
- Executed Ridge & Lasso CV which boosted score by approximately 5 basis points.  
- Test model on individual movies in different budget stratospheres.  


# Tools
1.  Web Scraping and Parsing:  Beautiful Soup
2.  Exploratory Data Analysis:  
       - Data Cleaning and manipulation:  Pandas, Numpy
       - Data Visualization:  Matplotlib, Seaborn
3.  Statistical Analysis:  Sci-Kit Learn, StatsModels

# Results Summary

Due to outliers the model proved to be very unstable in both tail ends, that is movies with very high budgets and movies
with very low budgets.  The Lasso model was settle on as it returned the same R^ 2 as Ridge but has the added benefit of 
being simpler and thus more interpretable.  

R^2 Summary by model type:
Log Transformation of target - 0.48
Baseline - 0.53
Polynomial Tranformation - 0.56
Quantitative + Dummy Variables = 0.59
Ridge & Lasso - 0.62

Due to a non-normally distributed target as well as a significant amount of outliers, the model did not perform well 
on movies with budgets in both ends of the tail.  It did, however, perform reasonably well when looking at movies in the
30-50 million budget range.  





