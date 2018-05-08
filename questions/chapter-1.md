### Statistics, Types of Variables

* Statistics is the study of how to best collect, analyze and draw conclusions from data.
* A summary statistic is a single number summarizing a large amount of data.
* We call the possible values of a categorical variable its "levels".
* If the values of a categorical variable have a natural ordering, it is called an "ordinal" variable. _Normal_ categorical variables without this property are called nominal variables.
* Variables are associated if their values move together. This association may not be linear, and could be negative (as one value moves up, the other moves down).
* If two variables are not associated, they are independent. There is no evident relationship to be derived between the two variables.
* What's the problem with anecdotal evidence? 1.) small number of cases, and 2.) not representative of the total population. Such evidence may be true and verifiable, but it may also represent extraordinary cases.

### Sampling

* In general, we always try to randomly select a sample from a population.
* With a simple random sample, each case in the population has an equal chance of being included and there is no implied connection between the cases in the sample.
* Non-response bias can affect the results of a sample. If you depend on people to get back to you, it's possible a subset of the population will reliably fail to respond. On the flip side, some subset of the population will generally respond more than others.


### Experiments

* We want to control any differences between the group. The only difference should be the treatment itself. Everything else should be the same.
* Randomization helps account for variables that cannot be controlled for. This can help prevent accidental bias from entering studies.
* Blocking refers to the assignment of cases into blocks prior to assignment into control and treatment groups. This is helpful when you suspect that other variables, in addition to the treatment itself, might influence the response variable. So if you were testing a new drug to reduce the risk of heart attacks, you might split the group into low and high-risk blocks, then randomly assign patients into control and treatment group. This ensures that the treatment group has an equal proportion of low and high-risk patients.

### Analyzing Numeric Data

* Scatterplot: provides a case-by-case view of data for two numeric variables.
* A dot plot is a one-variable scatter plot. It allows you to display the distribution of the values of a single variable.
* Histograms actually extend naturally from dot plots. We're still just showing the number of values of a variable across the range of values, but now we're grouping the values into natural bins. This makes it easier to count the number of data points within each bin (very tough to do with a dot plot).
* Histograms provide a view into the data density of a given variable. They are especially useful for describing the shape of a given distribution.
* If the distribution trails off in one direction, a distribution is said to have a long tail in that direction, and is skewed in that direction. So a common, power-law type distribution is said to have a long right tail, and is right-skewed.
* A mode is a prominent peak in a distribution. Distributions can be unimodal, bimodal, or multimodal.
* Standard deviation: how far away the typical observation is from the mean. This is the square root of the variance. This is useful at determining how close the data are, in general, to their mean.
* The distance from an observation and its mean is its deviation.
* For normally-distributed data, 70% of the data will typically be within one standard deviation of the mean, and 95% will be within two standard deviations.
* To articulate the distribution of data, it's helpful to provide the mean and standard deviation, but also the modality and the skew of the data. Very different distributions can have the same mean and standard deviation!
* Calculating variance and standard deviation are often means to an end: being able to estimate the uncertainty associated with a sample statistic.
* When there are an odd number of observations, the median is the observation that splits the data into two halves.
* When there are an even number of observations, the median is the average of the two obervations closest to the 50th percentile.
* Outliers help us 1.) identify strong skew in the distribution, 2.) identify data collection or entry errors, 3.) provide insight into interesting and unexpected properties of the data.
* Robust statistics (or robust estimates) are not affected drastically by extreme outliers (median, IQR are examples). The mean and standard deviation, on the other hand, can be affected significantly by outlier values.
* Skewed data are ripe for transformation! For instance, if it's clear that there are many values at the start or end of a tail, we may be able to take the log base 10 of these values, which may allow us to better visualize the distribution.
* Transformation can make the data much less skewed, and makes certain statistics less sensitive to extreme outliers.
* Transformation can also make it easier to apply a model (e.g. linear regression) on our data. Two variables may not have had a linear relationship before, but after transformation, they do!

### Analyzing Categorical Data

* A contingency table helps us see the number of records of a dataset with a given combination of two categorical variables ((spam, has number), (spam, has no number), (no spam, has number), (no span, has no number)). Adding a color to the number of records, where the intensity of the color is tied to the magnitude (effectively a heatmap) can help even more!
* A similar table for only one categorical variable is called a frequency table.
