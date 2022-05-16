---
layout: post
title:  "Deep learning course"
date:   2022-04-25 16:50:00 +0200
categories: posts
---

## Deep learning course
 
So there was some break after the first course, I wanted to learn about TensorFlow, a package for machine learning, a big one. It was a bit too big. I tried some tutorials, but I was lost… 

Right timing, mrdbourke started a new TensorFlow course. It was still in progress, but he was kind to share it on his GitHub. I went through them, as they were done. At the ending something appeared that made me curious. A certificate about deep learning models (well, TensorFlow). Don’t get me wrong, I’m not a big fan of certificates, still it was something to make my results real. I had some break after I went through the beta version of the course, later I restarted the course to get a better grasp of it. 

Learning from the machine learning projects’ challenges, this time instead learning the code, I started a small github project, to have the useful part of the code, some examples at one place [here]( https://github.com/CsLHegedus/Deep-learning-projects). It grew quite large with examples for subtasks, even with that I stopped doing it at the end of the transfer learning notebook. Why? Because natural language processing (nlp) and time series forecasting lessons were mostly just the re-use of previously introduced layers, techniques. On the other hand some really concept were detailed there.
## Let’s summarize the course. 

Disclaimer, I can’t really remember the order of these point exactly, I had to look them up.
## Warm-up tensors and fully connected (dense layer only) model

Before anything there was a refresher about tensors, shapes, dimension, the basics. It has begun with a single cell/unit/neuron, it wasn’t a deep learning model, just linear regression. I learned (again) about loss functions, optimizers, loss graphs. I said hello to some old friends, like Pandas, Matplotlib, Numpy, scikit-learn. Due the computational requirements, I learned to use Google Colab, that was basically the Jupiter Notebook with extra goodies (it offers free cpu and gpu time for training).  

The first deep model only had two layers, it was a simple Sequential model. The model complexity was a gradually building up, more cells, more fully connected/ dense layers, nonlinearity, shapes and others, I really liked how I built more and more complex models. First toy data sets, MNIST set, a prepared structured dataset. There was a table of more important hyperparameters for problem classes, quite useful as beginner. And a video [course](https://www.youtube.com/supported_browsers?next_url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DnjKP3FqW3Sk&feature=youtu.be) for the theoretical background, just enough to keep going. 
## Convolution neural networks with data augmentation 

How do you filter out important information of the pixels of an image? A new layer, called convolution, came in the picture. What it does (hint it emphasizes certain features, like vertical lines with a vertical edge detector), its more important parameters, like number of filters, strides, kernel_size. Another one called MaxPooling (it simply picks the most important features of the subarray, check this for the [details]( https://poloclub.github.io/cnn-explainer/)). 

The first pattern, Conv2D, Conv2D, MaxPooling, repeat. The first architecture, vgg16. It wasn’t much more than using the pattern I mentioned before, reshaping the output matrix into a vector with a Flatten layer, toss a dense layer at the end of it to get the output result. A nice simple model that worked on actual images. Not very well, but it worked.

How to improve it? Data augmentation is one way. Not all images are perfect shots, angles, sharpness, zoom range can vary. If your production data means that people shoot pictures you better teach your model to handle it to some extent. How? Modify your data with random rotations, cropping, zooming, flips, just to name a few. Here my best guess is that you use what you expect from the user, what sounds an awful idea if I think about it as an engineer student. 
## Transfer learning 

Image processing is computationally expensive. So expensive that smart people figured out, what if you could train a deep model on thousands of (more like million(s)) images and use that model for your specific task. It’s called transfer learning. Déjà vu, from the machine learning course, isn’t it?
## “As is” transfer learning

At first,there was the “as is” method, as mrdbourke called it. You just use the already trained model with your data preprocessing part. Not that useful, your data usually has minor differences compared to the data the pre-trained model was trained on.  It was the first time I used the functional API instead of a Sequential API
## Feature extraction notebook

At the second, there was the feature extraction. As an analogy, you want to decide, whether an image shows an orange or not. You could use a model that can recognize 1000 classes (oranges, apples, peaches…) to replace its final layer, so its only output is orange/ no orange. With other words it works well, if at least a subset of the data the model is very similar to yours, as above it’s a good way to save on bills that way. Also, you only need to train that last one or two dense (fully connected) layers.
It was the time to learn about callbacks, like TensorBoard to track your experiments, checkpoints, to save your model (actually only the weights, biases) while you train it, and early stopping.

One thing I missed was the two types of how can you use transfer learning in tensorflow. You can use tensorflow.keras.apllications, it’s literally inbuilt, very easy to use. On the other hand, the number of models is rather limited. Or you can use TensorflowHub, where you can find a much greater number of models. 
## Fine-tuning
	
So in feature extraction you only have to train the dense layers, but your data have to be very similar to the original the model was trained on. What if your data is still closely resembles the original data, but there are minor differences. You can train a model, you have already done it. Still you can’t re-train a state-of-the-art model, the whole deal was about that it is too expensive. 
The solution is compromise, you can re-train some layers of the pre-trained model, albeit with smaller learning rate. Note that you train the dense layers roughly first, otherwise it’d take unnecessarily long time if you initialize your (kernel) dense layer with some random numbers.
## Scaling and optimization

The last notebook was about the scaling of experiments. Let’s say you want to solve a multi class classification problem, like is there a cat, a dog, orange or another 497 types of things on the image, you have 1000 example per type (class). Let’s assume that only one of these can appear at once. 

First experiment: simplify the problem to one versus rest binary classification, try out a few classes with 1% of the examples. Use 10% of the classes, 1% data. 10% of the classes, 10% of the data. All classes 10% data. Final experiment with all classes and examples. Try out many things in small, drop the worse, narrow the number of possibilities, without guesses or use of “experience”. Not a bad method, still, I’m not sure that it works with short deadlines. With code re-usage, it probably does.

Up until now, it wasn’t a big issue if the model training wasn’t too fast. Let’s go through some techniques. 
* Apply functions on the data with map() to parallelize, ie. data preparation.
* Use batches.
* Use prefetch to preprocess data on multiple CPUs for better utilization of the GPU.
You can find the whole list [here]( https://github.com/mrdbourke/tensorflow-deep-learning/blob/main/07_food_vision_milestone_project_1.ipynb)
This part was the most enjoyable to me, next was natural language processing, oh dear...
## Natural language processing

Did I mention before that I’m more interested in scaling models than handcrafting features? It came back, haunting me here. So far I had most of the data in numerical form. Some One Hot encoding, some scaling was needed, nothing too bad.
Oh, about one hot encoding. So you have a corpus ( all your text) you split it into words, maybe remove punctuation, still all you have is a bunch of words. You say one hot encoding can turn categories into numbers. Yeah, we deal with many words. That leads to a huge number of columns, (features) in each row one „1” and a thousand „0”. Such a waste of memory, other tool is required!
## Tokenization and embedding

Word tokenization is a technique, where you say right, turn words into numbers, almost like in one hot encoding, instead here you say „apple is yummy” -> {1, 2, 3} „orange is yummy” -> {4, 2, 3}. Another important idea here is that you limit the number of words by the size of your vocab. Least common elements gets the identifier out of vocabulary ( OOV). Of course, you can do tokenization with characters too, but later about those.

So the text is in some form of numerical data, still not ready to use yet. In the second step, you should turn those into vectors. Similar words have similar vectors. Without details, you can train this layers, and yes, just like at images you can use pre-trained embeddings (actually this is just a few trained fully connected layer with a new name). Neat, isn’t it?
## 1D Conv neural network 

So finally you have some vectors. Each element (attribute) has some meaning. You have to filter out the important ones, highlight some. Isn’t that familiar? Yeah, you can use the good ol’ Conv1D layers with MaxPooling, just conv1D layers instead of conv2D. Same with pooling.



## Recurrent Neural Networks

Another strategy would be that if your task is something like to predict a word’s (obvious foreshadowing) meaning, you need context, like previous words. Like you won’t say „Tomato soup is delicious gearing”, well, not too often. You should add some memory to the model, to remember previous words. You could actually use this for any sequential data later on.

There are some implementations, like long short term memory (LSTM), or gated recurrent unit (GRU). From the training standpoint the first is more expensive, the second is better for deeper models. 
## Multiple input models and NLP

At this lesson, you’re introduced to actual raw data. It’s messy, it takes plenty of preparation to make it work. It took a long time to figure out this part. First is baseline model, if I forgot to mention it. You always need a simple model you can beat with more advanced one later on.

First,  you start with some easy sequential models here. One for character tokenization, one with word tokenization and word embedding, one positional data based model. Not to mention that you have to handcraft data preparation for each. Holy molly...

It was the time for the functional API to truly shine. You can use those sequential models, like you used models at transfer learning and combine them into one MEGA model, for much greater result. And longer processing time. And longer evaluation time for each example.

It didn’t seem that practical, anyway, it was awesome! „I re-created a model from a paper!”

## Time series forecasting

So far, the time samples weren’t that important. What if there is a cyclical phenomenon? Like each time when I cook something gets crispy, too crispy if you get what I mean. Or there is a trend, like I’m improving with cooking. You could use a model like that to predict the stocks and get rich (please, it’s sarcasm, don’t risk your money, the course have a few details why).

At this part the new thing was a different way to split the data into training and test set. Instead of shuffling and sampling here you do something like this: {1,2,3,4} -> {1, 2, 3}, {4}. So based on let’s say three data points, you try to predict the forth. The important part is that you use a set of data points (window) to predict a set of data points (horizon). You can even say you want to predict 9th data point based on first three (offset) but you’ll get even less reliable results, as many things can change during 4-8 data points.

Rest was nothing too crazy, Recurrent networks again, some new terms, new metrics, like scale independent ones. New thing was that LSTM can actually output a sequence of data optionally.

But there was one concept that was a game changer. Layer subclassing. You can create your custom layers, based on standard layers or just go crazy with a customized one... Image a layer with conv2D, pooling layer and „skip” that essentially lets the data go through that block without change (although it’s something you can do with Functional API as well). You’re not that far from creating a Residual Network or ResNet. It was one of the models I used at transfer learning. Nice!
## Summary       

This course was fun! I really liked the problems, it was quite a bit of challenge.

 






