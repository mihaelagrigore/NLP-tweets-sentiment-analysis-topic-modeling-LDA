# Social media research: topic modeling on tweets

I conducted a research study of the interaction and perception of different stakeholders of the education system with the international assesment PISA (Programme for International Student Assessment). More precisely, I set out to discover the answers to these research questions:  

*Research Question 1.*  How is the discussion around the PISA examination represented in Twitter discourse and how did the discourse evolve over time ?
*Research Question 2.* What is the demographic profile of the participants to this online conversation ?  

To answer these questions, I turned to social media, where all categories of stakeholders voice opinions (students, teachers, parents, institutions etc) and where information is freely available.

First, I scraped **all historical tweets** while filtering for specific keywords I identified as being relevant. This part is discussed in two separate works:
1. <a href='https://github.com/mihaelagrigore/Scraping-historical-tweets-without-Twitter-API'>Scraping historical tweets without Twitter API - using snscrape</a>
2. <a href='https://github.com/mihaelagrigore/Scraping-with-Twitter-Developer-API-for-Academics'>Scraping using Twitter API</a>, more precisely Twitter's Academic track which allows access to unlimited histoical tweets (no cap on how many tweets or how far you can go back in time when doing the data collection).

The two notebooks don't stop at scraping, they also deal with exploratory data analysis, data celaning and feature engineering.
I also performed <a href='https://github.com/mihaelagrigore/NLP-for-sentiment-analysis-of-tweets'>sentiment analysis</a>: I analysed different ways to preprocess tweets text before feeding it to sentiment analysis algorithms and I compared several algorithms to see which one seems to work better on tweets, a peculiar type of text data.

Here, though, I focus on topic modeling. I used Latent Dirichlet Allocation (LDA) after I first compute the best number of topics this data would most coherently cluster into. 

## Stage 1: Coherence Model
```
models.coherencemodel from gensim library
```
from the gensim library

"Calculates topic coherence for topic models. This is the implementation of the four stage topic coherence pipeline from the paper <a href='http://svn.aksw.org/papers/2015/WSDM_Topic_Evaluation/public.pdf'>Michael Roeder, Andreas Both and Alexander Hinneburg: 'Exploring the space of topic coherence measures'</a>"

## Stage 2: Latent Dirichlet Allocation (LDA)
```
models.LdaModel from gensim 
```

Latent Dirichlet Allocation (LDA) automatically discovers the semantic structure of texts by examining statistical co-occurrence patterns within a corpus of training documents (the tweets). These algorithms are unsupervised, which means no human input is necessary – you only need a corpus of plain text documents.

Once these statistical patterns are found, any plain text documents (sentence, phrase, word) can be succinctly expressed in the new, semantic representation and queried for topical similarity against other documents (words, phrases etc).

To sum up, what you will find in this repo:
1. PISA tweets analysis - topic coherence.ipynb -> trains and run a coherence model to find the best number of topics (n) for this particular corpus of tweets
2. PISA tweets analysis - topic modeling -> uses LDA model to find the structure of the n topics. More precisely LDA finds the distribution of words weights into each topic. Based on this and the content of each tweet, individual tweets can be labelled with a main topic.

![image](https://user-images.githubusercontent.com/38474985/153065216-7e65ce87-3219-44d2-87d2-908d6767bf8c.png)
