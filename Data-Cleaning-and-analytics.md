# Cleaning of Data

Summary of Modifications:

* Added a New Column

  Column Name: Sentiments
  Data Type: String
  Description: It checks the level of the ratings on a specific product and gives us the sentiments of the user regarding the product.
  
  Method:
  data['Ratings'] = data['Ratings'].astype(float)
  
  data.loc[data['Ratings'] >= 4, 'Sentiments'] = "Positive"
  
  data.loc[data['Ratings'] == 3, 'Sentiments'] = "Neutral"

  data.loc[data['Ratings'] < 3, 'Sentiments'] = "Negative"


* Removed the NaN values in the new column

  Method:
  data['Sentiments'].fillna("Negative", inplace=True)

  Columns affected: Sentiments

* New CSV file is available with the name "updates-d-dos.csv"


# Data Insights

First in the list is 

[D-DOS sentiment, price chart.pdf](https://github.com/user-attachments/files/18480132/D-DOS.sentiment.price.chart.pdf)

1) Count of sentiments in the whole dataset (pie chart)
2) Count of features in the form of donut chart
3) Sum of Ratings by name
4) Count of Price
