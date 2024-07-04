# Covid


# Predictive Insights for Resource Allocation in Healthcare

Our goal is to uncover predictive insights within our dataset to efficiently allocate resources such as staff and medical supplies across hospitals and the broader health sector, based on anticipated needs.

## Sections

- # Fetching Data
  - Due to GitHub file size limits, the data are separated into multiple datasets, organized by [year, semi-annual, or quarter].
- # Data Integrity
  - There are two issues with the above datasets.
- # Common Features across selected df(s)
  - Different models can be built, leveraging non-overlapping features. However, this wasn't undertaken due to time constraints.
- ### Concatenation of datasets
- # Data Cleaning & EDA
  - From df.describe(), we immediately notice negative values in the min row, which, after a careful reading of the provided README.md file for the datasets, does not make any sense. These must be human errors, and we need to address them.
- ### Human Errors
  - One might think it's negative because of a reduction in the population, but that is not the case, as shown in plots below.
  - Red dots are below zero, while blue dots are above zero.
- ### Handling Human Errors
  - Statistically, it doesn't make a significant difference whether we replace the negative values with their absolute values, the mean, median or mode over a certain period of time (2023-01 to 2023-09), or clip them to zero. It won't affect the standard deviation since the number of negative values is small, except for one value in 'New deaths per million', where taking abs() is not advisable. For instance, abs(-180) = 180, which still doesn't make sense.
- ### Null Values
  - Let's handle null values in the Income feature.
  - Filling with the mode is a bad idea because it will assign all NaN values (7.8%) to 'High income', thereby skewing the data.
- #### First approach: fill the Income based on past year(s).
- #### Second approach [Best approach]
  - Find a dataset that completes the gap.
  - Although this is the best approach, due to time constraints, I wasn't able to find a dataset that categorized countries' income the same as WHO.
- #### Third approach: random sampling
- #### Correlation
  - We want to remove features that are highly correlated with each other.
  - High correlation = [-1 to -0.8 , 0.8 to 1]
- ### Feature Engineering
  - It seems like we did a good job finding a relevant feature for Income, using cpm_income.
- ### More Feature Engineering
- ### Why I am not worried about multicollinearity
  - When using Univariate Time Series Models: By definition, you have only one feature.
- ### Naive Forecaster: Serving as a baseline
- ### Univariate Time Series Model
  - Hyperparameter Search:
- ### ML
  - Using 10 days to predict the next 2 days
- ### Future Work
