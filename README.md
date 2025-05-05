# Salesforcecast

RETAIL FASHION SALES DATA FROM ITALIAN FASHION COMPANY

Customer Classification:

As the k value increases the distance between the clusters and within the clusters decreases.

Cluster 0: "White & Blue Basics" (Highlights the strong presence of white and blue items)
Cluster 1: "Yellow & Technical Focus" (Emphasizes the yellow color and the interest in technical fabrics)
Cluster 2: "Yellow & Fluid Style" (Highlights the yellow color and the preference for fluid items)
Cluster 3: "White & Blue Inclined" (Similar to Cluster 0, indicating a tendency towards white and blue)

classified customers according to there taste in clothing.
Next we have classified according to the customer type:
classic buyers, luxury seekers, budget conciuous , trendy shoppers.

depends on the purchasing patterns:
Used qty, price, sales_before discount and sales after discount 

calculated the discount ratio and divided them into type of buyers
Cluster 0: High Quantity Buyers, Less Discount Sensitive, High Spenders
Cluster 1: Low Quantity Buyers, Less Discount Sensitive, Moderate/Low Spenders
Cluster 2: Low Quantity Buyers, Less Discount Sensitive, Moderate/Low Spenders
Cluster 3: High Quantity Buyers, Less Discount Sensitive, Moderate/Low Spenders


Observed highest number of sales in jan because of huge discounts.

KMeans algorithm added PCA for dimention reduction



Sales Forecasting:

I have used Sales and weather files to include seasonality in the ARIMA Model
A small number of clothing items are extremely popular and frequently bought, so they get restocked often.
Most items are not restocked or have low sales volume.

People tend to buy georgette frabric and black clothes and long and medium coats are pricey
------------------------------------------------------
---------------------------------------------------
--------------------------------------------

ARIMA :

Can handle seasonality: so first i have froupes columns according to seasons and month 
AW: Autumn/winter[next 6 months]
SS: spring and summer[jan to august]

calculates sales total sales per month and annual sales per season 

next  ihave mapped seasons and years
got aw17 aw18 aw19 ss17 ss18 ss19 and total sales :
this dataframe is a time series data whci can be used in in ARIMA Model for forecasting sales

ARIMA(1,1,1): (p,d,q)

AR:auto regressive : predicticts future value based on the past value 
model take sone previous value at the time series to predict the current value
Next D: Integrated[d]:
  Differencing means subtracting each value from the value came before it

MA: moving AVERAGE Q=1
one previous forecast to predict the current value.


so calcumation goes this way:
d=1 so it will subtract value from the previous sales,
p=1:predicts from the previous value[2019-2018]sales
q: past forecast error[when u take 2017 and 2018] we will predict the value for 2019 then this difference with actual value and out predicted value of 2019 will become the error rate.

Next Year Sales = (Constant) + (p * Previous Year Sales) + (q * Previous Year Prediction Error)

-------------------------------------------------------
-----------------------------------------------------
---------------------------------------------------------
-----------------------------------------------------

CUSTOMER CHURN:
The metrics you're referring to are performance evaluation metrics used to assess a classification model's effectiveness. Here's an explanation of each one:

1. Precision:
Definition: The proportion of true positive predictions out of all the predicted positives.

For class 0: 0.87 means that, when the model predicted a customer would not churn, 87% of those predictions were correct.

For class 1: 0.97 means that, when the model predicted a customer would churn, 97% of those predictions were correct.

2. Recall:
Definition: The proportion of true positives out of all the actual positives.

For class 0: 0.98 means that 98% of actual non-churn customers were correctly predicted as non-churn.

For class 1: 0.83 means that 83% of actual churn customers were correctly predicted as churn.

3. F1-Score:
Definition: The harmonic mean of precision and recall. It balances precision and recall, giving you a single metric for model performance.

For class 0: 0.92 is the F1-score, a balance of the 87% precision and 98% recall.

For class 1: 0.90 is the F1-score, balancing the 97% precision and 83% recall.

4. Support:
Definition: The number of true instances of each class in the dataset.

For class 0: There are 53 non-churn instances.

For class 1: There are 47 churn instances.

5. Accuracy:
Definition: The overall percentage of correct predictions.

0.91 means 91% of all predictions (for both classes) were correct.

6. Macro Average:
Definition: The average of precision, recall, and F1-score across all classes, treating each class equally.

Precision (0.92), Recall (0.91), F1-score (0.91) are the averages of the respective metrics for both classes.

7. Weighted Average:
Definition: The average of precision, recall, and F1-score, weighted by the support (i.e., the number of instances) of each class.

Precision (0.92), Recall (0.91), F1-score (0.91) are calculated by giving more weight to the class with more instances, ensuring that the larger class has more influence on the average.
