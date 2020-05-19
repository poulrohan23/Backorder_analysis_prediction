# Backorder_analysis_prediction
# Backgroud:
I am interested by advanced analytics related to supply chain, and decided to take on a modeling project to gain experience and better understand one particular challenge: predicting whether a product will go on backorder.

Product backorder may be the result of strong sales performance (e.g. the product is in such high demand that production cannot keep up with sales). However, backorders can upset consumers, lead to canceled orders and decreased customer loyalty. Companies want to avoid backorders, but also avoid overstocking every product (leading to higher inventory costs).

# Data
I used data from Kaggle, which had approx. 1.9 million observations of parts in an 8 week period. The source of the data is unreferenced.

# Outcome: whether the part went on backorder
# Predictors: Current inventory, sales history, forecasted sales, recommended stocking amount, part risk flags etc. (22 predictors in total)

# Modeling
# Key considerations of the data:
1. Imbalanced outcome: Only 0.7% of parts actually go on backorder.
2. Outliers and skewed predictors: Part quantities (stock, sales etc.) can be on very different scales.
3. Missing data: A few variables have data that are missing (not at random).
4. n>>p: There are many observations (1.9 million) relative to the number of predictors (22).

# Implemented Models
We made several modeling decisions to address these issues:

# Random forest :
1. Perform well with imbalanced data typically
2. Robust to outliers and the skewed predictors: Because they are using tree partitioning algorithms and not producing coefficient estimates, outliers and skewness are not as much of a concern as for other predictive models.
3. Dealing with missing data: The few variables with missing data had mean imputed, and a binary variable was created to indicate whether the observation had missing data, in hopes to account for the missing data not being random.

# Validation
1. KFold: We use 10-fold cross-validation in order to tune model parameters (maximum number of variables to try and minimum leaf size), as well as compare model performance.
2. The ROC Area Under the Curve (AUC) was used as a validation metric because the outcome is so imbalanced. By looking at ROC curves, we may determine a cutoff threshold for classification after fitting the models, rather than naively assuming a threshold of 0.5.






