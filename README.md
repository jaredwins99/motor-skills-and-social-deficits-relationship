# Analyzing and Modeling Motor Skills and Social Deficits and their Relationship in Children

This repository contains an R script with linear models for analyzing relationships between motor performance and social responsiveness across three different conditions: Typical Development, ADHD, and Autism.

To view the R presentation, download the HTML file ["Motor Skills and Social Deficits Presentation"](https://github.com/jaredwins99/motor-skills-and-social-deficits-relationship/blob/main/Motor%20Skills%20and%20Social%20Deficits%20Presentation.html) and open it in a browser.
Use arrow keys to scroll through the presentation.

## Research Question

Since movement impairments commonly co-occur in children alongside developmental disorders--including autism spectrum disorders (ASD) and attention-deficit/hyperactivity disorder (ADHD)--it is worthwhile to analyze the relationship between motor and social impairment.

## Most Relevant Data Features

- SRS_TotalRawScore: the social responsiveness scale attempts to ascertain a child's level of motivation to engage in social interactions, recognize emotional and interpersonal cues, and to interpret and respond to those cues appropraitely. Ranges from 0 to 195, with 195 reflecting severe social deficits.
- mABC_TotalStandardScore: the movement assesssment battery for children attempts to identify imapirments in various motor performance of children between the ages of 3 and 17 years old. There are three main categories: manual dexterity, aiming and catching, and balance.

## Modeling

Segmentation 

There was a discrepancy found in the conduction of the study by analyzing participants by ID, creating two regimes of social responsiveness score. The model required segmentation in the form of including the binary SRS_VERSION feature as a regressor.

Typically Developing Base Model:

- Data subsets were created focusing on specific metrics of interest.
- Developed models comparing social score versus only movement score.
- Incorporated an added variable: SRS_VERSION.
- Further explored the effect of age.

ADHD Model:

- Subsetted the data focusing on metrics like ADHD_Subtype, CurrentlyNotTakingMeds, and SecondaryDiagnosis.
- Created models emphasizing the impact of ADHD subtype and secondary diagnosis.

Autism Model:

- Initial models focus on the relationship between raw scores and total standard scores.
- Developed a comprehensive model incorporating SecondaryDiagnosis.

## Diagnostics

Assumption Checks and Hypothesis Testing:

- For each model, assumptions such as linearity and homoscedasticity were checked using visual plots.
- F-tests were conducted to compare different models.

## Results

Comparing Beta Estimates:

- Beta estimates across different conditions (typically developing, autism, ADHD) and versions (1 and 2) were compared visually.
- None of the estimates using version 2 of the social response scale proved to be statistically significant (95% confidence interval clearly crossing 0).
- The estimates from version 1 were potentially significant, and negative (increase in movement, leads to decrease in social responsiveness, i.e. better socialibility.
- From weakest to strongest relationship (value of beta coefficients), the estimated relationship between the two scores went typically developing (weakest), ADHD, autism (strongest).
- However, our confidence in the estimates followed the inverse relationship, from autism (loosest confidence interval), ADHD, to typically developing (tightest confidence interval).
- Overall, this reflects weak evidence that there is a relationship between movement impairment and social impairement, with largest practical significance being for children with autism.


Note:
This repository primarily uses the ggplot2 package for visualizations and the base R functions for linear modeling.
