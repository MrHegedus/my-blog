---
layout: post
title:  "Machine learning course"
date:   2022-04-18 20:24:00 +0200
categories: posts
---

## Machine learning course

So I was there, many hours of videos, plenty of code to go through and a discord channel. Let me walk through the tools I learned about, my opinion about them now a year or so later.

## Jupiter notebook and Conda

The first set of videos were about how to set up a working environment with Jupiter Notebook and Conda. 

Let’s start with Jupiter Notebooks, a tool, that helps you to code and get outputs, like images or text. Its important feature is that you can write code in so-called blocks. Write a bit of code, run it. It lacks a good debugger, but it’s a nice learning tool. 

You can use packages, like Matplotlib, Pandas, NumPy, but the challenge starts when you have teammates. You have your packages, your teammate might have different packages, or the same packages with different versions.

That’s the point where you need a package manager, like Conda. It takes away the hurdle to update these packages and let you save them to a simple file. It's called as environment, and you can send it to your team, so you can work with the same tools. One less potential source.

## Final thoughts

I don’t really use Jupiter notebooks anymore, still many other notebooks are built on it, like Kaggle or Google Colab (more about these a bit later), and so it was kind of useful to learn about it.

 Conda? I don’t really use it, because I don’t need it with Google Colab , still good to know such tools exists. It'll be probably important again when I start to use an IDE, (PyCharm) instead of Google Colab.

## Machine learning theory
 
 So I had the learning environment setup, next was some theory (Actually I don’t remember the order of these sections very well, anyway…). You can find the article here. The more important one was a 6-step framework for machine learning modelling with some extra:

 * Problem definition: can you even define your problem as a machine learning task, or something simpler solution, like a hard-coded decision tree is fine?
 
 * Data: what kind data is available, does it match with the problem, what kind of insight can I get with i.e. domain knowledge, is it supervised/unsupervised problem, assuming first, is it regression or classification, for more search for (early data exploration or EDA)
 
 * Evaluation: how do you define success, what kind of loss function describes the best that definition?
 
 * Features: What parts of data do I need? Can I use all or curse of dimensionality screws me. Do I need something like PCA (or a more advanced method) to reduce dimensionality? Can I combine feature to define better ones? (Like instead of some data in x, y coordinate system polar would be more meaningful for the model.)
 
 * Models: what model do I need? (scikit-learn cheat sheet), how does it compare to other models in accuracy, how long it takes to run the “learning” how fast can I do a prediction?
 
 * Experimentation: What should I try out? Do I get the desired i.e. accuracy results? Can I verify those results with checking actual predictions?

Another important part was the classification of the problems, just some example: 
* Supervised learning
	* Classification problems (samples, label pairs, like picture - Dog)  
		* Binary classification problem (is the person healthy or not, one vs rest)
		* Multi-class classification problem (is that an SUV pickup, or lorry, perhaps a bus)

* Unsupervised problems (samples only)
	* Clustering (create similar groups)

The data can be balanced at supervised problems, or not, and so many more. Check this for [more](https://whimsical.com/CA7f3ykvXpnJ9Az32vYXva).

## Pandas and Numpy

Pandas is a package for I/O, and data preparation for smaller databases (up to about 100 GB). I mostly used to import comma separated values (csv) , something you can get from almost any relational database, a few times JSON, a format often used by APIs. Its other use is to prepare your data, like one hot encode categorical data, choose the features you need. Pick it if your data has non-numerical values.

Numpy is a package for very fast computations with numbers, vectors and tensors, if you only have numerical data you may pick this.

## Matplotlib

A package to easily visualize you almost anything. Do you want to check your data’s distribution? Do you want to make a plot for the loss and other metrics? Use this. Easy to use, quite versatile, especially if you have some experience with Matlab (I had).

## Scikit-learn

A machine learning package with premade and easy to use data preparation and models.
You can create a nice pipeline, or just use its column transformer to do many steps of data preparation with one tool. It also has a very handy cheat-sheet.

## Finally modelling 

After the tasks above, it was time for the “end to end” examples. Everything from the data preparation, modeling, evaluation in one. One regression problem and one classification. Majority of the work was the preparation of the data, at first with pandas, later with scikit-learn, after that visualize, plot loss curves with matplotlib, evaluate the result. 

I’m not sure, but I think that was the time when I learned about pipelines, a way to prepare similar data easily. Next I picked some models and tried out them. For details, check out the course material [here](). 

That was the end for structured data models, then unstructured data came. It was a transfer learning example for images. That tutorial was very different from the others, it came from nowhere. It was interesting, still, I didn’t see how I could continue from there. 

## Summary 
I was quite satisfied with the course I picked, but the machine learning had larger emphasis on data preparations, feature crafting, “handcrafting”, a common pattern with smaller datasets. 
I was more interested in the modelling, especially the deep learning part. 
It seemed more experimental, more challenging. Later I found PyTorch codes that made machine learning problems very easy with reports and everything. Things I wrote by hand, so I wanted to go for image processing, something that I was interested since the university. 
