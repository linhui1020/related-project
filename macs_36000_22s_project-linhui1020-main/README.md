### MACS-36000 "Computational Methods Using Online Social Media Data" Final Project

Please upload your slides, shared link to your recording, code, and final report to your GitHub classroom (here), name it as **36000_YourFirstLastName**.

Please upload the shared **link** to your recording here: 

https://drive.google.com/file/d/1kcCgMnQv8ypGLI1Ho1BUpk0nFDzn1yLi/view?usp=sharing
----------------------


## Project Summary

This research project intends to investigate 1) Does characters with higher degrees have higher accuracy in link prediction? 2) What are the similarities and differences between the communities detected from Marvel Universe network (MU) and the communities from comments associated with each character? The significance of the research questions provides a comparative analysis of how the social network construction in this artificial world, especially the appearance of social ties, and encourages Marvel creators and writers of later generations for content creation through analyzing existing Marvel Universe Network and social media comments to continue this magic world. Furthermore, understanding the how characters are distributed and are connect with each other in the Marvel Universe, one of keys of Marvel’s success, provides inspiration for comic creators, movie script writer and content creators for creative work beyond Marvel Universe. 

---------

## Folder and file introduction

## I Data folder contains all data file required in this project. The data in my research project can be divided into two parts - Marvel Universe network and Reddit comments corresponding to characters

1) hero-network.csv: Marvel Universe network is retrieved from the Kaggle platform. The Marvel Universe network contains nodes and edges between nodes; Link of original dataset: https://www.kaggle.com/datasets/csanhueza/the-marvel-universe-social-network?datasetId=741

 2) Web scraping Reddit.ipynb: Reddit Pushshift API to scrape comments which contain the name of the corresponding character from the subreddit “AskforScience”

3) Scrap-result.json: This json file includes all comments scraped from the reddit platform

4) top100_hero.txt: This file contains the characters with highest degrees in Marvel Universe network

## II Analysis folder contains analysis method for two dataset. Link prediction and community detection for Marvel Network. Community detection for the comment data. 

###  1) Analysis for network data: network based link prediction and community detection.ipynb

### Step one: load the network data "Marvel-network-edges.csv"

### Step two: calculate the degree distribution and plot

![](social%20media%20project%20pictures/degree%20distribution.png))

### Step three: select the 100 characters with higest degrees

![](social%20media%20project%20pictures/top_100_subgraph.png)

### Step four: Link prediction, use Adam-Adar rank to calculate the link prediction accuracy of each node by randomly removing 50% existing edges of that node, then generate the predicted links and calculate the matching accuracy with true links. 

![](social%20media%20project%20pictures/degrees%20and%20average%20accuracy.png)

### Step five: exclude nodes with worse link prediction accuracy (<40%), calculate the average accuracy for the nodes with same degrees

### Step six: polynomial transformation of standardized degrees and OLS linear regression

![](social%20media%20project%20pictures/fuction.png)

### Step seven: calculate the eigenvectors of nodes in the network structure

### Step eight: use elbow method to determine the number of clusters and then do k-means clustering based on eigenvectors for characters

![](social%20media%20project%20pictures/top100%20community%20separate.png)

-----------------

###  2) Analysis for comment data: Topic-based & Semantic community detection.ipynb

### Step one: load the comment data from json file 

### Step two: tokenized and normalized corpus

### Step three: LDA topic modeling, select 10 topics based on coherence score; refer to the several highest probability comments of each topic to have a better definition of each topic

### Step four: For each comment, label the topic based on the highest probability. Calculate the topic frequencies for each character, and label the character based on the most frequent topic

### Step five: if two characters share with the similar topic, then build a connection between these two characters

![](social%20media%20project%20pictures/community_comments_topic.png)

### Step six: employ pretrained Google news vectors negative 300.bin Word2Vec model to find the embedding vector of each comment, represent each character as the average word embedding vector of associated comments

### Step seven: use the elbow method to determine the best numbers of k for k-means clustering of average word embedding vector of each character

![](social%20media%20project%20pictures/community_wordembedding.png)

### Step eight: For each character, using consine similarity between the character with other characters. Plot the heatmap for a visualization of similarities between characters

![](social%20media%20project%20pictures/pairwise%20similarity.png)
