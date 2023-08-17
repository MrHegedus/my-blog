---
layout: post
title:  "Milestone project"
date:   2023-08-17 08:53:00 +0100
categories: posts
---

## Milestone project
Hey there! Many things happened since I checked in. 
I am long overdue for a milestone project for deep learning.

I'll use The Hundred-Page Machine Learning Book (2019) by Andriy Burkov
as a template. An old book by IT standards? Yes. The tools mentioned there might be outdated, 
but it is still useful as a template.

Let's outline a relatively simple project. Nothing new here. I wanted to implement this idea for a while.

## Project description:
Create a solution for an Android telephone, that takes a photo 
of 1-8 symbols and returns the name of the symbol and a short description.
Use the cloud for the computation. 

Constraints (subject to changes as the project develops): 
* 75% accuracy. 
* 10% false positives at worst case.
* max 5 seconds from taking the photo to the results
* $50 dollars budget
* 40 workhours budget (45 min screen time per hour)

## Engineering project description:
Find a toy dataset and set up a baseline model for classification. 
Use a state of art model with the toy dataset.
Create a small custom dataset, and increase the number of labeled images until
desired benchmarks are achieved.
Deploy the model to a cloud service.
