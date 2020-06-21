---
title: Identifying Emerging Market Segments with k-means
author: Andrew Hetherington
date: '2020-06-14'
slug: emerging-market-segments-kmeans
categories:
  - Data Science
  - Machine Learning
tags:
description: 'How data can help in the aftermath of a pandemic'
---

![](/page/2020-06-14-r-rmarkdown_files/oc-gonzalez-xg8z_KhSorQ-unsplash.jpg)

**EY’s [Future Consumer Index](https://www.ey.com/en_gl/consumer-products-retail/how-covid-19-could-change-consumer-behavior)** is a short, 8-minute read that pulls together the results of a survey of 4,859 consumers across the US, Canada, UK, France and Germany during the week of 6 April 2020.  Using some rather snazzy data visualisation techniques, EY proposes the emergence of five distinct types of consumer in the aftermath of the Covid-19 pandemic, each with differing behaviours and sentiment in regard to their purchasing decisions.  Some of these types are pessimistic—cutting deep their expenditures—while some are greatly optimistic, jumping at the opportunity to spend more as restrictions are gradually lifted.

It’s not clear exactly how EY defines these five types (“get to normal”, “cautiously extravagant”, “stay frugal”, “keep cutting”, and “back with a bang”) beyond general qualitative descriptions.  However, it did get me thinking.  Two of the key variables EY have considered are *optimism* and *income*.  Clearly, optimism relates to how willing a consumer is to spend and income relates to how able they are to do so—and both will feed into an individual’s purchasing decisions.  Suppose that we had access to quantitative data on consumers’ relative levels of optimism and income.  How could we divide consumers up into groups, based on these data, in a rigorous and reproducible way?  

### The k-means algorithm

[K-means clustering](https://en.wikipedia.org/wiki/K-means_clustering) is a method that classifies a number of points into k groups.  Briefly, the algorithm searches a space for k “centroids” and allocates each data point to one of these centroids.  The algorithm then iterates over and over, aiming to minimise the variance within each cluster.  In this way, we eventually find k groups which are (hopefully) distinct and reflect the true natures of the groups within the data. 
To illustrate, let’s create a dataset in which there are five groups of 100 consumers each.  Suppose that each group has a typical level of income and optimism, with some natural variation around these values.  We could represent the situation graphically like so:



```{r labelled data}
[...] # Set seed and generate data for 100 consumers from each group

incomes <- cbind(normal_incomes, extravagant_incomes, frugal_incomes, 
                 cutting_incomes, bang_incomes)

optimisms <- cbind(normal_optimisms, extravagant_optimisms, frugal_optimisms, 
                   cutting_optimisms, bang_optimisms)

colours <- c("red", "blue", "green", "orange", "purple")

# Set up an empty plotting area
plot(NULL, xlim=c(0,100), ylim=c(0,100), xlab="Income", ylab="Optimism",
     main="500 surveyed consumers, labelled")

# Plot data points
for (i in 1:5){
  points(incomes[,i], optimisms[,i], col=colours[i], pch=3)
}

[...] # Add legend
```

![](/page/2020-06-14-r-rmarkdown_files/Labelled_500.png)

The case of having two variables is particularly straightforward to think about as each point lives somewhere in this 2D income–optimism “space”. However, the k-means algorithm can be applied in an arbitrary number of dimensions — that is, we could just as easily expand our model to include a third variable (perhaps one relating to the country in which a consumer lives, as different governments have effected different measures to deal with the virus), a fourth one, and beyond.

Of course, in the real world we wouldn’t know the characteristics of the groups beforehand — and we wouldn’t even know how many groups there were! So momentarily forget what I’ve told you so far and see if you can divide the following data points up into groups:

![](/page/2020-06-14-r-rmarkdown_files/Unlabelled_500.png)

Not quite so simple, is it? It’s definitely possible to identify some clusters, but how many are there and where does one cluster end and another begin? Ask ten different people and you will get ten different answers. But with k-means, we can take a mathematical, data-driven approach that will give the same answer each time. Let’s apply the algorithm and see what we get:

```{r fit model}
[...] # Aggregate data into one matrix with incomes in the first column 
and optimisms in the second

# Fit model using k-means
model <- kmeans(data[,1:2], centers=5)# Retreive centroids

centroids <- model$centers
centroids

#     income optimism
# 1 68.76713 58.50722
# 2 43.95596 57.64992
# 3 65.51750 83.71031
# 4 34.73630 34.00436
# 5 39.11255 89.01036

# Retreive clusters
clusters <- model$cluster
clusters

# [1] 2 2 1 2 2 2 2 2 2 3 2 2 2 2 2 2 2 2 2 2 2 1 2 2 2 2 2 2 2 2 2 2 2 
2 5 2 2 2 2 2 2 2 2 2 2 5 2 2 2 2 4 2 2 2 2 2 2 4 2 5 2 2 2 2 2 2 2 2 2
2 5 2 2 5 2 5 1 2 2 2 2 2 4 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 1 1 1 1 ...
```

We can see that, as asked, k-means has found us five centroids and has classified each data point into one of five clusters, based on its distance from the centroid. Let’s plot our results to get a better understanding:

```{r model results}
# Add k-means cluster result to the data
data <- cbind(data, clusters)

# Define function to map cluster number to a colour
map_colours <- function(num){
  colours[num]
}

# Apply function to data
clusters_colours <- lapply(clusters, map_colours)

# Set up empty plotting area    
plot(NULL, xlim=c(0,100), ylim=c(0,100), xlab="Income", ylab="Optimism")

# Plot data points
for (i in 1:500){
  points(data[i,1], data[i,2], col=colours[as.integer(data[i,4])], pch=3)
}
```

![](/page/2020-06-14-r-rmarkdown_files/Kmeans_result_v3.png)

And finally, a side-by-side comparison:

![](/page/2020-06-14-r-rmarkdown_files/Comparison.png)

We can see that k-means has done a pretty good job overall — the algorithm has been able to pick out the general characteristics of the five groups in terms of optimism and income. In this example, we have the ground truth to hand so we can see that k-means has grouped some of the more pessimistic “cautiously extravagant” consumers into the bulk of the “stay frugal” cluster. Although we know that k-means has got this aspect of the problem “wrong”, there are undoubtedly areas of overlap between the five types of consumer. This may even prove to be a useful insight — the algorithm has pointed out a similarity between these consumers that we may not have picked up on otherwise.

### Conclusion

The k-means algorithm [does have its limitations](https://stats.stackexchange.com/questions/133656/how-to-understand-the-drawbacks-of-k-means) but it can reveal patterns and trends in data that may not be immediately visible to the human eye. This is why clustering algorithms are so often used in [exploratory data analysis](https://en.wikipedia.org/wiki/Exploratory_data_analysis) when we’re seeking to understand a new and unfamiliar dataset. We continue to produce data at an astounding rate whenever we make purchases — and you can bet that there will be no end of analysts using techniques just like this in hopes of making sense of it all as economies gradually recover in a post-pandemic world.

### More info and credits

**Andrew Hetherington** is an actuary-in-training and data enthusiast based in London, UK.

* Connect with me on [LinkedIn](https://www.linkedin.com/in/andrewmhetherington).
* Follow me on [Medium](https://medium.com/@andrew.m.hetherington).
* See what I’m tinkering with on [GitHub](https://github.com/andrewhetherington/python-projects).
* The notebook used to produce the work in this article can be found [here](https://github.com/andrewhetherington/python-projects/blob/master/Blog%E2%80%94Emerging%20market%20segments%20with%20k-means/Blog%E2%80%94Detecting%20emerging%20market%20segments%20with%20k-means.ipynb).

Images: Photo by [OC Gonzalez](https://unsplash.com/@ocvisual?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/s/photos/sunrise?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText).

All plots and code outputs were created by the author using [R](https://www.r-project.org/about.html) and [RStudio](https://rstudio.com/).