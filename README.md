# Robert Pattinson's Acting Career Analysis using Sentiment Analysis and LSTM Neural Network in Tensorflow
![robert](https://user-images.githubusercontent.com/98130185/158734863-34639b65-86d3-4448-b0a9-a14e48286989.jpeg)

***Hi~ Gorgeous.***

## Background
4th March 2022 was the first day Batman was released in SF. As a previous fan of Twilight(Book), I was also a fan of Robert Pattinson even if the movie was not good at all. After many years, Batman was the second movie I saw starred by Robert Pattinson. Unfortunately, I fell asleep too many times because I think it was boring. 

So I'm wondering what he has been doing all these years, why every movie I saw is bad. This led me to do this project, to check what his career looks like based on people's perspectives.

## Objective
The goal is to portray Robert Pattinson's acting career based on people's perspectives on each of his movies using **Web Scraping, EDA, Sentiment Analysis, and Classification models**.

## Data Source
Use **Selenium** and **BeautifulSoup** to scrape the audience reviews and critics reviews from [IMDb](https://www.imdb.com/name/nm1500155/?ref_=fn_al_nm_1) and [Meta Critics](https://www.imdb.com/title/tt1877830/criticreviews?ref_=tt_ov_rt) of every movie Robert Pattinson stared in.

As a result, we have 8060 audience reviews and 945 critic review.

## Structure
### Robert's Career Overview
- In total, Robert Pattinson acted in 38 movies from 2004 to 2022. Every year, he would shoot at least 1 movie. On average, he would star in 2 movies per year.
<img width="423" alt="image" src="https://user-images.githubusercontent.com/98130185/160049880-34202ec5-df52-49e1-8864-d43e9b7e1378.png">

- Nearly 79% of movies he participated in were as a leading role, and this trend becomes more obvious in recent years, at least one movie a year that he starred is as a leading role.

<img width="210" alt="image" src="https://user-images.githubusercontent.com/98130185/160050085-b3600830-c681-4415-9e17-efa0644b0780.png"><img width="343" alt="image" src="https://user-images.githubusercontent.com/98130185/160050183-ed80b2d8-61da-4e52-9e30-02685affb296.png"> 

- Movies' average rating is 6.3/10.0, but people's reviews of his films are getting better.
- Critics's reviews are harsher than audience's in general.
- Movies that audiences like that but critics don't are movies in 2016, 2017, and 2020, which are The Lost City of Z, Good Time, and Tenet.
(Because 3 old movies do not have Meta Critics score, we set them as 0.)
<img width="468" alt="image" src="https://user-images.githubusercontent.com/98130185/160050589-01614e34-a749-4904-85f7-febd6db72fcb.png">

### Sentiment Analysis
The plots show the frequencies of words's sentiment.

More Blue -> More positive (Greater positive frequencies)
More Red -> More negative (Greater positive frequencies)
More White -> More neural (Similar positive and negative frequencies)

***To see the interactive visualization, please download the 2 files in this repo named as "Interactive Visualization".***

<img width="800" alt="image" src="https://user-images.githubusercontent.com/98130185/160050788-396f3f96-0af5-4fec-ad48-0c38b3c58da7.png">

<img width="800" alt="image" src="https://user-images.githubusercontent.com/98130185/160052233-88ec84c4-9f1a-4e70-97de-b5e04342f6d7.png">

### Prediction Models
4 models were used to explore the classification accuracy from easy to complex ones.

They are **Logistic Regression**, **Random Forest Classifier**, **LightGBM Classifier**, **LSTM (long Short Term Memory) Neural Network**.

Before fitting the model, we found that Meta Critics data was imbalanced. We choosed **UnderSampling** method instead of **SMOTE** to fix the imbalance to avoid the overfitting because of the artificially generated new data. After experimenting on the ‘sampling strategy’, which is the desired ratio of minority class number / majority class number, 0.9 yielded the best result.

### Model Comparison

For audience's reviews from IMDb, LightGBM yielded the best result.

<img width="457" alt="image" src="https://user-images.githubusercontent.com/98130185/160059078-1e3ca1f5-1837-4ce5-8bea-7136edb364ea.png">

For critics's reviews from Meta Critics, LSTM yielded the best result.

<img width="457" alt="image" src="https://user-images.githubusercontent.com/98130185/160059100-23feb9bc-cc1e-4844-8fb9-1965b27a0ac2.png">
