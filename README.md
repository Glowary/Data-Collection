# Mars Data Scraping

## Part 1: Scrape Titles and Preview Text from Mars News

1\. Import the necessary libraries, including Splinter, BeautifulSoup, and Pandas.  
2\. Use Splinter to automate browsing to the Mars News website, then inspect the page and identify the elements.  
3\. Create a Beautiful Soup object to parse the HTML content of the page.  
4\. Extract the titles and preview text of the news articles by identifying the HTML elements containing this information:

```py
text_elements = mars_news_soup.find_all('div', class\_='list_text')  
for texts in text_elements:  
  print(texts.text)
```

5\. Store each title and preview in a Python dictionary with keys 'title' and 'preview'.  

```py
for element in text_elements:
  title = element.find('div', class\_='content_title').get_text()  
  preview = element.find('div', class\_='article_teaser_body').get_text()  
  news_dict = {'title': title, 'preview': preview}  
```

6\. Append these dictionaries to a list, and print the list of dictionaries to see the results.  

## Part 2: Scrape and Analyze Mars Weather Data

1\. Import the necessary libraries, including Splinter, BeautifulSoup, Pandas, and Matplotlib for data visualization.  
2\. Use Splinter to automate browsing to the Mars Temperature Data Site. Create a Beautiful Soup object to parse the HTML content of the page. Identify the HTML table with the data. Extract the data from the HTML table.  
3\. Assemble the scraped data into a Pandas DataFrame. Ensure that the columns have the correct headings and data types. Use `astype` and `to_datetime` as needed to convert data types.

```py
df\['terrestrial_date'\] = pd.to_datetime(df\['terrestrial_date'\])  
df\['sol'\] = df\['sol'\].astype(int)  
df\['ls'\] = df\['ls'\].astype(float)  
df\['month'\] = df\['month'\].astype(int)  
df\['min_temp'\] = df\['min_temp'\].astype(float)  
df\['pressure'\] = df\['pressure'\].astype(float)
```

4\. Analyze the dataset to answer the provided questions about Mars weather data.

- Use `.nunique()` function to find the number of months and days worth of data in the dataset.  
- To find the coldest and the warmest months on Mars and the lowest and the highest atmospheric pressure:  
  - First, find the average daily temperature or atmospheric pressure for all of the months.  
  - Then find the max and min value of the dataset to find the number of Earth days in a Martian year.
  
5\. Export the DataFrame to a CSV file.  

*References*  
[Converting Dataframe](https://stackoverflow.com/questions/38067704/how-to-change-the-datetime-format-in-pandas)  
[Pandas Dataframe](https://www.w3schools.com/python/pandas/pandas_ref_dataframe.asp)
