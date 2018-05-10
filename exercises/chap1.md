* [Link to Lab](http://htmlpreview.github.io/?https://github.com/andrewpbray/oiLabs-base-R/blob/master/intro_to_data/intro_to_data.html)
* [Link to data](https://www.cdc.gov/brfss/)

First, I converted the CDC BRFSS data into a tibble like so:

    library("tidyverse")
    cdct <- as_tibble(cdc)

### Exercise 1

How many cases are there in the dataset?

* Printing the `cdct` tibble shows that there are 20,000 cases, each with 9 variables.
* We can also retrieve the number of rows in our tibble using `nrow(cdct)`.

To get a frequency table of occurrences of smokers vs. non-smokers in the study, run

    table(cdct$smoke100) * 100 / nrow(cdct)

We can plot the percentage of smokers and non-smokers in the survey using the `geom_bar` geometry and the `..prop..` computed statistic:

    ggplot(cdct, aes(smoke100)) + geom_bar(aes(y = ..prop.. * 100)) + ylab("Percentage of Survey") + xlab("Smoked > 100 cigarettes")

A simpler bar plot, with better categorical labels for smokers vs. non:
    
    barplot(table(cdct$smoke100))

### Exercise 2

The `IQR` function can get us the inter-quartile range for a given column of a data frame:

    IQR(cdct$height)

We can create mosaic plots in R:

    mosaicplot(table(cdct$gender, cdct$smoke100))

This breaks out our data first by gender, then by smoking status.

### Exercise 3

At first glance, our mosaic plot above indicates a higher percantage of male smokers vs. femaleo

`dim(df)` gives us the dimensions of a data frame!

`cdct[1, 1]` lets us extract the first variable from the first observation. Since I've converted our original data frame to a tibble, this returns a tibble.

To get the weights of the first 10 participants, we can run `cdct[1:10, 6]`.

We can get all variables tied to the first 10 observations by running `cdct[1:10,]`, leaving out the second index.

We can subset our data frame using the `subset` command, which accepts the data frame we want to filter and the condition (which returns a boolean vector), e.g.

    subset(cdct, cdct$age > 50)

We can use the `&` and `|` operators for and and or, respectively, e.g.

    subset(cdct, cdct$age > 50 & cdct$weight > 200)

### Exercise 4

Create a new object called `under23_and_smoke` that contains all observations of respondents under the age of 23 that have smoked 100 cigarettes in their lifetime.

We can visualize the distribution of height by gender using a nice boxplot:

    ggplot(cdct, aes(gender, height)) + geom_boxplot() + coord_flip()

We can compare the exercise status of respondents with their BMI:

    ggplot(cdct, aes(as.factor(exerany), bmi)) + geom_boxplot() + coord_flip()

### Exercise 5

Let's make a histogram of age:

    ggplot(cdct, aes(age)) + geom_histogram(binwidth=10)

You can flip between different plots by clicking the left and right arrows in the top-right corner of our plot window in RStudio!

### On your own

_Make a scatterplot of weight versus desired weight. Describe the relationship between these two variables._

This is a pretty interesting scatter plot of weight vs desired weight:

    ggplot(cdct, aes(weight, wtdesire, color=gender)) + geom_point()

In general, people's weight is higher than their desired weight, but we can be more precise about this (see below).

_Let’s consider a new variable: the difference between desired weight (wtdesire) and current weight (weight). Create this new variable by subtracting the two columns in the data frame and assigning them to a new object called wdiff._

    wtdiff <- cdct$weight - cdct$wtdesire

_Describe the distribution of wdiff in terms of its center, shape, and spread, including any plots you use. What does this tell us about how people feel about their current weight?_

* The distribution is unimodal, with a slight left skew. The `IQR` is 21, spanning from 0 to 21, suggesting that most people are between the weight they desire and 20 pounds above it. The average person (here we use the median to describe the average given the skew and extreme outliers) weighs 10 lbs more than they want.

_Using numerical summaries and a side-by-side box plot, determine if men tend to view their weight differently than women._

Yes, women have a higher positive difference between their weight and desired weight. We can compare this using the following boxplot:

     ggplot(subset(cdct, cdct$weight - cdct$wtdesire > -200), aes(gender, weight - wtdesire)) + geom_boxplot()

_Now it’s time to get creative. Find the mean and standard deviation of weight and determine what proportion of the weights are within one standard deviation of the mean._

    subset(cdct, mean(cdct$weight) - sd(cdct$weight) < cdct$weight & cdct$weight > mean(cdct$weight) + sd(cdct$weight))
