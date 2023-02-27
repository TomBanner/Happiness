

![Map](/images/Happy.jpg)

In this project I am going to be analysing the World Happiness Report to try to determine trends in happiness around the world, as well as finding out more about the factors that influence global happiness.  

The World Happiness Report is an annual publication that measures the happiness levels of countries around the world based on various factors such as economic growth, social support, freedom to make life choices, generosity, and trust in government and business institutions. 

Here is a description of the factors that are analysed in the report:

Life Ladder: the overall happiness score for each country in the dataset. It is calculated by asking people to rate their current life situation on a scale of 0 to 10, where 0 represents the worst possible life and 10 represents the best possible life.

Log GDP per capita: the natural logarithm of a country's gross domestic product (GDP) per capita, which is a measure of a country's economic output divided by its population. It is used as a proxy for a country's standard of living, with higher values indicating greater economic prosperity.

Social support: the extent to which people feel supported by family, friends, and other social networks. It is measured by asking people about the social support they receive and is used as an indicator of the social and emotional connections that contribute to overall well-being.

Healthy life expectancy at birth: the number of years a newborn can expect to live in good health, based on data from the World Health Organization. It is used as an indicator of the quality of a country's healthcare system and the overall health of its population.

Freedom to make life choices: the extent to which people feel they have the freedom to make important life decisions. It is measured by asking people whether they feel they have the freedom to choose what they do with their lives, and is used as an indicator of personal autonomy and agency.

Generosity: the extent to which people donate money or time to charitable causes. It is measured by asking people about their charitable giving and is used as an indicator of pro-social behavior and civic engagement.

Perceptions of corruption: the extent to which people believe corruption is prevalent in their country's government and business institutions. It is measured by asking people about their perceptions of corruption and is used as an indicator of the quality of governance and institutional trust.

Positive affect: the extent to which people experience positive emotions such as happiness, joy, and contentment. It is measured by asking people about their emotional experiences and is used as an indicator of subjective well-being.

Negative affect: the extent to which people experience negative emotions such as sadness, anger, and stress. It is measured by asking people about their emotional experiences and is used as an indicator of subjective well-being.

Confidence in national government: the extent to which people trust their country's national government. It is measured by asking people about their confidence in their government and is used as an indicator of institutional trust and political stability.


.............................................................................

 
  

# Analysing the data with SQL and Python 

To get started I set up a connection with the database.

# Correlations

 I ran a query to load all of the data into a dataframe in order to explore the coorelations between the factors. I then highlighted cells based on the strength and direction of the correlation, to create a correlation heat map.

Red indicates a negative correlation with happiness, and green indicates a positive correlation. The darker the colour, the stronger the correlation.

![Corr](/images/df_corr.png)

.............................................................................

# More SQL Queries

Next I ran a few more queries which you can explore in my notebook. 

One of them was to find which countries had the highest average life ladder score in the past 5 years and which had the lowest.

Here are the 10 happiest countries over the last 5 years:

![Hap](/images/happyy_df.png)


Here are the 10 unhappiest countries over the last 5 years:

![Sad](/images/sad_df.png)

.............................................................................

# Linear Regression

Next I ran a linear resgression using sklearn to determine which factors influence happiness the most.

![Coef](/images/coef_df.png)

We can see the strongest influence on happiness is social support, one unit increase in social support creates a 3 unit increase in happiness. 

The next strongest influence on happiness is freedom to make life choices, one unit increase in freedom to make life choices creates a 2 unit increase in happiness. 

The strongest negative influence on happiness is Perceptions of corruption, a 1 unit increase in Perceptions of corruption decreases happiness by 1.5 units.

.............................................................................

# Sentiment Analysis

Next I am going to do sentmient analysis to explore if there is correlation between the sentiment of the news and the happiness score of that country. 

I used the News API to scrape the top news storys for each country and then performed sentiment analysis on the results using nltk.

In order to get a more accurate sentiment score, I limited my search to English speaking countries only.

Here are my results:

![Sent](/images/sentiment_df.png)

We can see that the most negative news comes from the UK! Not surpising ;)



Next I ran an SQL query to select just the English speaking countries and their happiness scores and loaded into a dataframe. Then I merged the dataframes so that I could calculate the correlation between news sentiment and happiness.

![Mer](/images/merged_df.png)

I then calculated the correlation. 

Correlation between Average Sentiment and Average Life Ladder: 0.0511

We can see that there is a weak correlation.

I wanted to analyse more countries to get a larger dataset but i ran out of API requests.

At the bottom of my notebook are a lot of other requests that I did for sentiment analysis, however I have used all of my requests for the News API.

.............................................................................


# Preparing for Tableau

Next I created 2 CSV files that I can use to work with in Tableau.
One which only includes the countries where I have all the data from 2017-2021, and another one with all of the data.

.............................................................................

# Tableau

To begin with I created an overview page by loading all of the data. The page is interactive so you can reordeer factors ascending or descending to see which countries have the highest and lowest factors. 

![Overview](/images/Overview.jpg)

.............................................................................

Then I created a 'Happiness Map' of the world. The darker the colour, the happier the country.
![Map](/images/Happiness_Map.jpg)

.............................................................................

Next I created a series of graphs to explore some of the relationships between the factors. 

.............................................................................

Here I plotted average freedom to make life choices against life ladder.

![fh](/images/freedom_happiness.jpg)
We can see that greater freedom is leads to greater happpiness.

.............................................................................

Here I plotted average freedom to make life choices against wealth:

![fw](/images/freedom_wealth.jpg)

We can see that greater freedom is also leads to greater wealth.

.............................................................................

Here I plotted average social support against happiness:

![sh](/images/social_happiness.jpg)

We can see that social support has a significant positive influence on happiness.

.............................................................................

Here I plotted GDP against happiness:

![wh](/images/wealth_happiness.jpg)

Even though it is often said that money doesn't equal happiness, we can see that wealthier countries are in fact generally happier than poorer ones.

.............................................................................


Here I plotted GDP against health:

![wh](/images/wealth_health.jpg)

We can see that wealth is positively correlated with health. 


.............................................................................


Finally, I plotted social support against health:

![whe](/images/wealth_health.jpg)

We can see that, not only does social support improve happiness, but it even improves health. 

.............................................................................

Lastly I combined all these graphs into a dashboard where you can see all the relationships together:

![d](/images/Dashboard.jpg)

.............................................................................


You can view my Tableau files here:
https://public.tableau.com/app/profile/tom.banner7232

Enjoy :)
