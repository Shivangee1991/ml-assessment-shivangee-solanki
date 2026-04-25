*******************************************
Part B: Business Case Analysis
*******************************************
B1--> Problem Formulation
---------------------------------
(a) ML Problem
---------------------------------
Target:
items_sold (how many items are sold per store per month)
Inputs (features):
Store size, location type
Promotion type (discount, BOGO, etc.)
Month, weekends, festivals
Past sales data
Type:
Regression
Reason:
Because we are predicting a number (items sold), not categories.

--------------------------------------
(b) Why items sold instead of revenue
--------------------------------------
Revenue depends on prices and discounts
A promotion may increase sales but reduce revenue
We actually want to see which promotion increases demand

Main point:
Always choose a target that matches the real business goal.

---------------------------------------
(c) Better approach than one model
---------------------------------------
Instead of one model, use:
Separate models for urban, semi-urban, rural stores

Why:
Different stores behave differently
One model may miss these differences

--------------------------------------
B2--> Data and EDA strategy
--------------------------------------
(a) Data joining
-----------------

We have: Transactions, Store data, Promotion data, Calendar data

Join using: store_id, date, 

Final data: One row = one store per month

We calculate: Total items sold, Avg footfall, Promotion count

--------------------
(b) EDA steps
--------------------
Bar chart (sales vs promotion): → Which promotion works best

Line chart (monthly sales): → Check trends and seasonality

Box plot (store type): → Compare urban vs rural

Heatmap (correlation): → See which features matter

Histogram (sales): → Check skewness/outliers

Why:
Helps understand data before modelling.

--------------------
(c) Imbalance issue
--------------------

80% data has no promotion

Problem: Model may ignore promotions

Solution: Give more weight to promotion data, Balance dataset, Or train separate model

---------------------------------------------
B3. Mode Evaluation and Deployment
---------------------------------------------
(a) Train-test split
----------------------
Use time-based split
Train = old data
Test = recent data

Why not random: It mixes future with past → wrong results

Metrics: MAE → average error
         RMSE → big errors matter more
         R² → how well model fits

---------------------------------         
(b) Explaining model decisions
---------------------------------

Use feature importance / SHAP

Example: 
December → festivals → loyalty points work
March → normal time → discounts work

Explain simply:
Show what factors influenced the decision.

---------------------------------
(c) Deployment
---------------------------------
Save model (joblib/pickle)
Every month: Prepare new data, Run model and Try all promotions → pick best one

Automation: Run monthly

Monitoring: Check prediction vs actual If error increases → retrain

This helps the company choose the best promotion using data instead of guesswork.