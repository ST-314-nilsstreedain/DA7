# Data Analysis 7 - Lizard Species
A 1987 study compared the speeds at which two lizard species (Sagebrush lizards and Western fence lizards) could complete a maze. The speeds, in meters per second, to complete a maze was recorded for 26 Sagebrush lizards and 22 Western fence lizards.

The data are below. You may either copy and paste the data lines of code below or download and open the lizards.R script on Canvas to bring this data into R. You do not need to import a csv file for this week’s assignment. Run both the Sagebrush and Western_fence lines to store the vectors of speeds in R.
```
Sagebrush <- c(1.74, 1.41, 1.30, 1.42, 2.23, 1.67, 1.15, 1.38, 1.75, 1.47,
               1.59, 1.99, 2.21, 1.41, 1.70, 1.89, 1.80, 2.02, 1.87, 1.75,
               1.15, 1.63, 1.84, 1.20, 1.28, 1.08)

Western_fence <- c(1.52, 1.74, 1.79, 2.01, 3.13, 2.89, 2.56, 2.65, 3.38, 2.36,
               2.21, 1.65, 2.05, 2.84, 3.36, 2.02, 1.63, 2.51, 2.18, 2.09,
               1.82, 2.53)
```

1. (1 point) In this assignment you’ll estimate and test the difference in the average speeds of the two lizard species to complete the maze. Write a question of interest for which a two-sided t test for the difference in populations means can be used to answer.
```
Does the sample of lizards provide evidence that the average speed of a
Sagebrush lizard is different from the average speed of a Western fence lizard?
```

2. Compute summary statistics for each sample.
  - (1.5 points) Report the sample mean, sample standard deviation, and sample size for the sampled maze speeds of Sagebrush lizards. Hint: use the mean(), sd(), and length() functions in R to do this.
```
𝑥𝑆 = 1.612692
𝑠𝑠 = 0.3241056
𝑛𝑠 = 26
```

  - (1.5 points) Report the sample mean, sample standard deviation, and sample size for the sampled maze speeds of Western fence lizards. Hint: use the mean(), sd(), and length() functions in R to do this.
```
𝑥𝑊 = 2.314545
𝑠𝑊 = 0.5554983
𝑛𝑊 = 22
```

3. (1 point) The parameter of interest is the difference in the population means of maze speeds for Sagebrush and Western fence lizards, 𝜇𝑆 −𝜇𝑊. Using the sampled data, calculate the point estimate for this parameter of interest.
```
Point Estimate = μS − μW
= 1.612692 - 2.314545
= -0.701865
```

4. (1 point) The point estimate in the previous problem has an associated estimate for the standard error. Calculate this standard error estimate and report the value below.
```
Standard Error = ((sd1^2/n1) + (sd2^2/n2))^1/2
= ((0.3241056^2/26) + (0.5554983^2/22))^1/2
= ((0.10504445291/26) + (0.30857838352/22))^1/2
= (0.00404017126 + 0.01402629016)^1/2
= 0.01806646142^1/2
= 0.13441153752
```

5. (1 point) The point estimate reported in question 3 also has an associated degrees of freedom. Using one of the two tools provided in the Week 8 module on Canvas for calculating Satterthwaite degrees of freedom, calculate the degrees of freedom for this point estimate.
```
Degrees of Freedom = ((sd1^2/n1) + (sd2^2/n2))^2 / ((sd1^2/n1)^2/(n1 - 1)
  + (sd2^2/n2)^2/(n2 - 1))
= ((0.3241056^2/26) + (0.5554983^2/22))^2 / ((0.3241056^2/26)^2/(25)
  + (0.5554983^2/22)^2/(21))
= ((0.10504445291/26) + (0.30857838352/22))^2 / ((0.10504445291/26)^2/25
  + (0.30857838352/22)^2/21)
= (0.00404017126 + 0.01402629016)^2 / (0.00404017126^2/25 + 0.01402629016^2/21
= 0.01806646142^2 / (0.00001632298/25 + 0.00019673681/21)
= 0.00032639702 / (0.0000006529192 + 0.00000936841952)
= 32.57020136
```

6. (2 points) Construct a 90% confidence interval for the difference in the average maze speeds of the two lizard species. Report the numerical values for the lower and upper bounds of the interval. Show your work.
```
Interval = -0.701865 +- 1.645(0.13441153752)
= -0.701865 +- 0.22110697922
= [-0.92297197922, -0.48075802078]
```

7. (2 points) Set up the null and alternative hypotheses needed to answer the two sided question of interest from question 1.
```
H0: μdiff = 0
Ha: μdiff ≠ 0
```

8. (2 points) Below is a side-by-side boxplot of the maze speeds for the two species. Use the boxplot to assess the sample size condition required to perform a two sample t test for the difference in population means.
<img width="403" alt="Screen Shot 2022-05-26 at 11 10 31 AM" src="https://user-images.githubusercontent.com/25465133/170549729-9514e566-8628-4d4c-b19b-9244bc70d857.png">
```
The distribution is relatively normal so a size of >= 1 for each sample is
sufficient.
```

9. (2 points) Using the sample statistics determined in question 2, calculate the test statistic for the two sample t test for the difference in population means.
```
t = -0.701865/0.13441153752
= -5.22176156117
```

10.  (2 points) Using the degrees of freedom from question 5 and the test statistic from the previous question, calculate the p-value. Hint: sketch the curve and shade in the p-value!
```
p = pt(-5.22176156117, 32.57020136)
= 4.968084e-06
```

11.  (2 points) Using the p-value from the previous problem, complete the following p-value interpretation by filling the blanks.
```
The probability of observing a difference in sample means of -0.2313927 or a
difference even more extreme is 4.968084e-06, when the null hypothesis is true.
```

12.  (4 points) Write a 4-part conclusion to answer the question of interest. Use a α= 0.1 significance level.
```
H0: μdiff = 0
Ha: μdiff ≠ 0

Test-statistic: -5.22176156117
P-value: 4.968084e-06

We reject the null hypothesis H0: μdiff = 0 because the p-value is less than the
significance level (0.1). Our sample data provides sufficient evidence that the
average speed of a Sagebrush lizard is significantly different from the average
speed of a Western fence lizard
```

## Gradescope Page Matching (2 points)
When you upload your PDF file to Gradescope, you will need to match each question on this assignment to the correct pages. Video instructions for doing this are available in the Start Here module on Canvas on the page “Submitting Assignments in Gradescope”. Failure to follow these instructions will result in a 2-point deduction on your assignment grade. Match this page to outline item “Gradescope Page Matching”.
