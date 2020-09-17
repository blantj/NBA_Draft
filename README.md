# NBA Draft
## Introduction
I set out to build a classification model that could predict whether an NBA draft prospect would have a succeesful career based upon their NCAA statistics and NBA Draft Combine measurements.  This would help NBA GMs solve the business problem of choosing which prospects to draft based on their probabilty of succeeding in the NBA.  I scraped prospect NCAA and NBA statistics from Basketball Reference and obtained NBA Draft Combine measurements in Excel form from Data.World.  I merged the 3 data sets together, dropping prospects missing from one or more of the datasets, which yielded 361 datapoints across the 2009-2017 draft years.  I modeled the data with K Nearest Neighbor Classification, Decision Tree Classification, Random Forest Classification.  All 3 models outperformed the baseline model considerably, with Random Forest Regression performing best on the primary success metric of Precision, with a Testing score of .52.

## Obtain Data
I scraped NBA career statistics from Basketball Reference for all 540 players drafted in the 2009 through 2017 NBA drafts. I also scraped final season NCAA Basketball Statistics from Basketball Reference for all 370 2009-2017 draftees that played college basketball.  Finally, I obtained measurements for all 517 participants in the same seasons' NBA Draft Combines in Excel Form from Data.World.  After three three data sources were merged using an inner join, the final dataset contained 361 data points. 

## Scrub Data
I went through several steps to scrub my data into a usable format.  First, I replaced missing values from NCAA and NBA statistics with the 0 values that NA represented.  For missing draft combine measurements, I created functions to calculate estimates for those values based upon non-missing correlated features for those players.  Finally, I calculated interactions to create additional features.

## Explore Data
In the process of performing EDA, I discovered that many of the Draft Combine measurements were very similar and highly correlated.  While the types of modeling that I used for this project did not necessitate removing correlated variables, this insight informed my expectations for number of influential features in my modeling.  I also discovered that many features had non-linear relationships with probability of success in the NBA.  Once again, the types of modeling that I used did not necessitate linear relationships between independent and dependent variables, so I did not attempt to make these relationships linear.

## Model Data
I used Precision as my principle evaluation metric in order to determine the model that would maximize the probability of selecting a succesful NBA draftee.  I used an 80/20 Train Test Split to validate my models.  A Stratified Dummy Regressor produced a Testing Precision of .23.  My next model, K Nearest Neighbor, had a Precision of .45.  I improved upon this with Logistic Regression, which produced a Precision of .50.  My top performing model a Random Forest model using Gridsearch CV, which had a Precision of .52.  Random Forest also produced an Accuracy of .67 and an F1 score of .44.

## Analyze Results
The top performing model, Random Forest, was useful in predicting the career success of NBA draftees.  Its precision of .52 outperformed the Dummy Regressor testing set Precision of .23 and was higher than the 25.7% percent of datapoints that were part of the positive class.


## Next steps
With more time, I would like to train an XGBoost model, which while more computationally expensive has the potential to produce better results than my existing models.  I would also like to explore creating additional feature interactions to see if these can improve performance.

# Github Files
[nba_draft_modeling.ipynb](https://github.com/blantj/NBA_Draft/blob/master/nba_draft_modeling.ipynb) :  NBA Draft Modeling

# Sources
Basketball Reference: https://www.basketball-reference.com/

Data World: https://data.world/achou/nba-draft-combine-measurements

