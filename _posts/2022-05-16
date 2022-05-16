---
layout: post
title: "First team project"
date:   2022-05-16 18:16:00 +0200
categories: posts
---

## First team project 

It happened during the end of the supervised section of the course. I was fairly confident, that I can handle a task like this. I had two options, do it alone, or in a team. Furthermore, I wanted to taste what teamwork is like with programming. The course had a discord room that was exactly for that.

It took some time to find a partner, the plan was a bit bigger team, we ended up as a two member group. So the task was a recommendation system demo, a bit like a proof of concept in engineering. There was just one problem, I didn’t really know how those work. Well, I knew one method, singular value decomposition (SVD). 

How? I like video games and in one of my favorite games there was an interesting new mechanic. You could create an item with randomized parameters. The problem was that how do you value such, often unique items. For some reason, after some videos about models I was convinced that it used SVD. In reality the answer was a support vector regressor (SVR)[ https://mutaplasmid.space/faq/] model. Still, I learned something new!

Well, my partner was more experienced, she suggested a restaurant recommender dataset (Yelp), and she found a package for these recommendation systems (Surprise). There was also a nice card system (Trello) we used to divide the task into subtasks and set deadlines. It was neat.

So first step was data preparation. I had no experience with the package, so I actually started with step zero, I tried out the documentation’s examples, and reverse engineered them, to get insights.  Later we both started to work on the restaurant dataset, with different approaches. She went head on the task, I went to Kaggle for examples. 

We both had the same challenge, the dataset was too large to read in memory! Pandas came to help us, it has a feature that it reads in the dataset in batches, as I found out in a Kaggle project. One sub-task done. 

There was a problem, I had all the features, a small percentage of the dataset to work with, still I couldn’t plug it into the models, it wrote an error message I didn’t really understand. Stack Overflow didn’t help either. It was quite a bit of time when I said okay, check the algorithms, at least SVD step by step, maybe it helps. NG. Andrew had an excellent [video series]( https://www.youtube.com/watch?v=CS4cs9xVecg&list=PLpFsSf5Dm-pd5d3rjNtIXUHT-v7bdaEIe) machine and deep learning algorithms.

It was for explicit recommendations, the models were more about predicting how would someone rate a restaurant, thus it didn’t require all the features, just the restaurant name and rating of each customer, a huge sparse tensor. Did you guess what the error was? No? It was incorrect input shape.

I reverse engineered the data processing code from the Kaggle example (it had nested dictionaries, something new to me) for nothing! This was the first time I used k-fold evaluation, although totally unnecessarily, too.

Next was to run all the models with small scale experiments, keep the better ones, scale up, rinse repeat with large scale. It worked. I made reasonable predictions, albeit with larger than expected errors (I used accuracy that time). 

There was just one step left, fine-tuning. Easy-peasy isn’t it? I had two tools, randomSearch and gridSearch. Random search meant that I can try out more parameter combinations, gridSearch was to try out all combination with a few option for each hyperparameter. The model had much better accuracy, but the test predictions made no sense at all. 

It took quite a bit of time again, the answer came from a towardsdatascience article. My simple evaluation metrics were wrong for the task! I needed a custom one. That was the point where we suspended the project. It was a bit anticlimactic ending, but it was good enough as a proof of concept. Mission successful in my book. Sadly, I couldn’t continue with a new one, because of a training for my job took most of my time after that.





