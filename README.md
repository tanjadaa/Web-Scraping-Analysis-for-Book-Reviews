# Web Scraping & Analyzing Text for Book Reviews

## Table of Contents

### Introduction
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Project Overview
  
### Web Scraping
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Part 1: Scraping book attributes	

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Part 2: Scraping book reviews	

### Exploratory Analysis	
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Question 1:	

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Question 2:	

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Question 3:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Question 4:	

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Question 5:	

### Text Analysis	
### Word Cloud	
### Sentiment Analysis	
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Polarity Graph:	

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Subjectivity Graph:	
### Results	
### Conclusion	
### References	


### Introduction 
Book reviews make books a known quantity. They decrease the risk to readers that a particular book will be not what they had in mind at all. In fact, book reviews help potential readers become familiar with what a book is about, give them an idea of how they themselves might react to it and determine whether this particular book will be the right book for them right now.

Book reviews save readers time, prepare them for what they will find and offer them a greater chance of connecting with a particular book, even before they read the first page. Book reviews give books greater visibility and a greater chance for the authors getting found by more readers. Reviews help books to be more discoverable and credible and thereby boost sales and generate revenue for publishers and authors.

Hence it really crucial to examine these reviews and analyze their content in order to understand book sales and predict their market performance. 


### Project Overview 
The website www.booksaremagic.com is for a local bookstore in Cobble Hill, Brooklyn. Owned by best-selling author Emma Straub and her husband Michael Fusco-Straub, Books Are Magic is home to exciting new releases and beloved classics, hidey-holes for children and books to read in them, gumballs filled with poetry, readings and panels almost every night of the week and storytimes on the weekends, and yes, plenty of magic.

Our project goal is to scrape book attributes and reviews for the top 10,000 most popular and available books from www.booksaremagic.com and to analyze the generated datasets. The main idea is to answer whether critic reviews have an influence on readers and a subsequent effect on book sales?

The roadmap for the project consists of the following steps: Scrape data from the website, Cleanse it through appropriate operations, Perform Exploratory Data Analysis using Tableau, Perform Text Analysis using python libraries such Natural Language ToolKit (NLTK), TextBlob etc. to gain meaningful insights and discover valuable results


### Web Scraping 
To scrape "BooksAreMagic.com", we used Selenium - an automated scraping tool, PhantomJS - a headless browser and BeautifulSoup - a python library. For web scraping, we analyzed the website and selected only books from the Popular book list and all books that are available and in stock. We decided to exclude all future releases since those books won’t have any reviews.

![image](https://user-images.githubusercontent.com/57735006/112031163-66c7b100-8b11-11eb-8cde-4cbb05f7e170.png)


### Part 1: Scraping book attributes

We selected the top 10,000 most popular available books using selenium for book selection and page navigation. Using Beautiful Soup, we extracted attributes for each book. The following attributes were scraped: Book Title, Author, Price, Sales Rank (Ranking based on the number of copies of sold. Lower the rank, higher the number of books sold by the respective publisher/author), Genre, Published Month, Published Year.

After successfully scraping 200 pages from the website, the dataset generate consists of 7 columns & 10,000 rows.

![image](https://user-images.githubusercontent.com/57735006/112031307-8fe84180-8b11-11eb-81ad-22fe0249f126.png)

### Part 2: Scraping book reviews

On Inspecting the website, it can be observed that all elements under the review pane originate from hyperlinks where the review content are saved and loaded in json format. Using Beautiful Soup, all reviews were scraped and the review column consisted of all reviews, merged together for a single book. For text analysis it was essential to split all the reviews into separate rows for each book using pandas and other python libraries.

The scraped dataset consists of top 10,000 book titles, Links and all their reviews merged into a single row.

![image](https://user-images.githubusercontent.com/57735006/112031361-a098b780-8b11-11eb-9ffd-d2a1acfe0c39.png)


After splitting and separating the review for each book, the dataset finally consisted of approximately 112,000 rows for text analysis. 


![image](https://user-images.githubusercontent.com/57735006/112031393-a9898900-8b11-11eb-93a6-af5e585bdc8c.png)



### Exploratory Analysis

We performed EDA using Tableau to answer 5 most relevant questions.
#### Question 1: 
Which month has the most number of books published?
Ans: As evident from the graph, the month September followed by the month of October has the most number of books published. A possible explanation for this rise might be that these months are pre cursor to the holiday season where more books are sold.
#### Question 2: 
Which month has the highest sales rank for books? 
Ans:The month of November produces the book with highest sales rank

![image](https://user-images.githubusercontent.com/57735006/112031460-c1610d00-8b11-11eb-91ad-b6340acef0d7.png)


#### Question 3: 

What are the most published genres? 

Ans: Juvenile Fiction, Fiction, Juvenile Non-Fiction, Biography & Autography are few of the most published genres

![image](https://user-images.githubusercontent.com/57735006/112031514-cfaf2900-8b11-11eb-91a1-45ed101db759.png)


#### Question 4: 
What are the most expensive priced genres? 
Ans: The most expensive book genre is art followed by cooking.


![image](https://user-images.githubusercontent.com/57735006/112031550-da69be00-8b11-11eb-92dc-ba53ca434c08.png)


#### Question 5: 

How does the price vary across the years for genres?
Ans: The graph depicts how the average price for genres has fluctuated across the years. Poetry and Juvenile fiction based books have had the most fluctuation in prices through the years.

![image](https://user-images.githubusercontent.com/57735006/112031665-f66d5f80-8b11-11eb-8095-09671d779b81.png)


### Text Analysis
We performed text analysis on the scraped dataset from web scarping part 2. We used the 112,000 rows of reviews which was scraped for the top 10,000 books. The main idea was to get the sentiment measures for each review, group it by the book title, compute average sentiment value and merge it with the book attributes dataset for further analysis. 

The following python libraries were used for text analysis:
#### Re - To deal with all string and text related regular expression operations.
#### NLTK - For symbolic & statistical natural language processing of the English language.
#### ScikitLearn - To represent the text and string data into arrays and vectors form.
#### TextBlob - For processing textual data, speech tagging, noun phrase extraction, and sentiment analysis.
#### WordCloud - Open source library to visually represent textual data.

The following preprocessing operation were carried out before text analysis :
Cleansing text, Lemmatization, Stemmatization and Removing stopwords.

For text analysis, we used the 112,000 rows of reviews which was scraped. 

![image](https://user-images.githubusercontent.com/57735006/112031784-17ce4b80-8b12-11eb-9562-977dc042beb8.png)


Reviews with sentiment value.

![image](https://user-images.githubusercontent.com/57735006/112031810-1e5cc300-8b12-11eb-8872-a1f72d595abd.png)


Book attribute dataset and Book reviews dataset merged together

![image](https://user-images.githubusercontent.com/57735006/112031826-24eb3a80-8b12-11eb-84b1-4c742369ab55.png)


The most frequent words in the reviews column are displayed and meaningless words were added to create a custom stopwords list.


![image](https://user-images.githubusercontent.com/57735006/112031859-2ae11b80-8b12-11eb-838c-ad1b1bfc8f03.png)


### Word Cloud

The image depicts the most frequent words in the reviews section. Bigger and bolder words mean more repetitive words.

![image](https://user-images.githubusercontent.com/57735006/112031903-37657400-8b12-11eb-90b5-92076284f421.png)


### Sentiment Analysis

Using TextBlob Library, we computed to the sentiment measures values for each review. The key aspect of sentiment analysis is to analyze a body of text for understanding the opinion expressed by it. The sentiment measures consist of polarity and subjectivity values. 

Polarity is a measure which represents the levels of positivity in a text. Its a float value ranging from -1 to 1. 

Subjectivity is a measure which represents the levels of subject relevance in a text. Its a float value ranging from 0 to 1. For our project, we decided to filter out all reviews below a subjectivity of 0.1.

We grouping the sentiment value for each reviews by Book Title to get an aggregated value which was later merged to the book attribute dataset. 

After sentiment analysis, it was observed that most of the reviews were positive and with high subjectivity. The following graph depicts the polarity and subjectivity measures.

#### Polarity Graph:

![image](https://user-images.githubusercontent.com/57735006/112031967-48ae8080-8b12-11eb-826a-9641a0de3268.png)


#### Subjectivity Graph:

![image](https://user-images.githubusercontent.com/57735006/112031980-4cda9e00-8b12-11eb-9d40-addec935b5a1.png)



#### Results:

In order to analyze the sentiment measures and compare with sales performance for each book, we grouped the sentiment value for each reviews by its Book Title to get an aggregated value and merged it to the book attribute dataset. To derive final results, we compared the polarity values for each book to its sales rank using Tableau. 

The following graph compares the mean polarity versus the sales rank for the top 100 ranked books. Ideally, the polarity values should have decreased as the sales rank increased. But as observed from the graph, the general trend line depicts a gradual increase in polarity values as sales rank increase. Thus it can be summarized that a 
##### positive critic review doesn’t guarantee a success for a book in terms of sales and alternatively, critic reviews don’t have a major influence in book sales.

![image](https://user-images.githubusercontent.com/57735006/112032146-73003e00-8b12-11eb-8c73-0e0e48d41ab0.png)


Using tableau we analyzed further to inspect whether critic reviews are genre/theme subjective. 


![image](https://user-images.githubusercontent.com/57735006/112032163-798eb580-8b12-11eb-91a6-519d27c82287.png)

It’s interesting from the graph to observe that 
##### critic reviews are subjective when it comes to reviews across different genres. For genres, politics and poetry, the general trend line decreases ie Polarity value decreases as rank increases which means critic reviews do have an influence over sales for these genres. 

### Conclusion
This project was successfully implemented and the following goals were achieved:
1) Web scraping www.booksaremagic.com for Books Attributes & Book Reviews.
2) Performed EDA using the scraped dataset.
3) Answered key questions using text analysis:	 
Do critic reviews have a major influence in sales? 
Are critics reviews genre - biased?

Few challenges faced were:
The volume of data scraped was large and scraping dynamic JavaScript elements along with book attributes was very time consuming. This problem was solved by automating selenium using headless Phantom JS browser.
Dealing with fields that have no book attributes/no reviews.
As the scraping consisted of two parts and two different datasets were generated, combining the scraped book attribute dataset and the book review dataset for analysis was tedious

Future Scope: 
Due to the limited time, this project was carried out only for book reviews. The project can be extended by scraping and performing same analysis operation on author description and author reviews section to yield interesting results.


### References:
1 www.booksaremagic.net/ : Website from datasets were scraped for top 10,000 books
Sentimental Analysis of Book Reviews using Unsupervised Semantic Orientation and Supervised Machine Learning Approaches 

2 https://ieeexplore.ieee.org/document/8753089 

3 https://thisiswriting.com/why-are-book-reviews-important-for-authors/

4 crummy.com/software/BeautifulSoup/bs4/doc/

5 https://www.nltk.org/












