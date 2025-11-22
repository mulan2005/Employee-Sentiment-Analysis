Employee Sentiment Analysis

This project studies internal employee email messages to understand their overall sentiment and engagement levels.
Using NLP and data analysis, the project identifies how employees communicate, who shows positive or negative patterns, and which employees may be at risk based on their message behavior.

The project includes:

Labeling each email as Positive, Neutral, or Negative
Performing exploratory data analysis (EDA)
Calculating monthly sentiment scores for every employee
Ranking employees based on these scores
Detecting flight-risk employees
Building a linear regression model to study sentiment trends

Dataset
The dataset used is test.csv, which contains internal employee emails.

Key columns:
employee_id – who sent the email
message – the text body of the email
date – when the email was sent

Additional columns created during analysis:

sentiment – Positive / Neutral / Negative

sentiment_score – numeric score (+1 / 0 / -1)

month, message_length, etc.

Methods
1. Sentiment Labeling

Used a pretrained transformer model:
cardiffnlp/twitter-roberta-base-sentiment-latest
Applied the model to every message

Assigned each as:
Positive
Neutral
Negative

Saved the output in a new sentiment column

2. Exploratory Data Analysis (EDA)

Performed basic data exploration to understand structure and patterns, including:

Sentiment distribution across all messages
Distribution of message lengths
Monthly trends in sentiment
Examples of insights you can fill in:

3. Monthly Sentiment Score

Scoring rules per message:
Positive = +1
Neutral = 0
Negative = –1

For each employee per month, the following were calculated:

Total monthly score
Number of messages
Number of positive, negative, and neutral emails
Average message length

4. Employee Ranking

Employees were ranked each month using monthly_score.

5. Flight Risk Identification

An employee is considered a flight risk if:
They send 4 or more negative emails within any rolling 30-day window.

Process:
Filter negative messages
Group by employee
Apply a 30-day rolling count
Flag employees crossing the threshold

Employees flagged as flight risks:

6. Predictive Modeling (Linear Regression)

A linear regression model was built to understand what factors influence monthly scores.

Target variable:
monthly_score
Features used:

msg_count
avg_message_length
pos_count
neg_count
neu_count

Interpretation:

Positive coefficients → increase the score
Negative coefficients → decrease the score (e.g., many negative messages)

How to Run the Project

Open employee_sentiment_analysis.ipynb in Google Colab or Jupyter Notebook

Upload test.csv to the same environment

Run all cells in order
Output plots will be saved in the visualization/ folder

Visualizations Included
The following plots are saved inside the visualization folder:

sentiment_distribution.png
message_length_distribution.png
monthly_sentiment_trend.png
top3_positive_latest.png
top3_negative_latest.png
actual_vs_predicted.png
