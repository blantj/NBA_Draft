# NBA_Draft

In order to determine which factors predict draftee success in the NBA, I modeled a range of draft combine and college basketball stats versus success in the NBA.  The threshold for a succesful player was set at a career average of 9 points per game in at least 100 game appearances.  I used Precision as the primary evaluation metric in order to create a model with the goal of helping teams draft succesful players.  My data sources were NCAA Basketball stats from Sports Reference, Draft Combine stats from Draft Express and NBA stats from Basketball Reference.  Random Forest was the best model with a Precision of .52, followed by Logistic Regression with a precision of .50 and KNN with a Precision of .45.

# Documents

nba_draft_modeling.ipynb - Includes data cleaning and modeling associated with this project.
