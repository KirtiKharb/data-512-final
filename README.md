# Impact of the workplace environment on Mental Health

## Final Project Proposal

### Motivation/Problem statement:
Mental health has become a serious concern in the 21st century. As people in technical jobs lead a sedentary lifestyle and have very few social engagements outside their workplace, It is important to study the factors in a workplace that affect an individual’s mental health. I want to know how employers can take measures to promote their employee’s mental health and spread awareness to address this growing concern. Aside from company policies with regard to health, leaves, insurance, etc., the ability to comfortably communicate health problems with colleagues and supervisors can have a serious impact on an employee’s mental health.  

### Datasets:
For this project, I will use following dataset that is publicly available on [Kaggle](https://www.kaggle.com/).
- [OSMI Mental Health In Tech Survey 2014](https://www.kaggle.com/osmi/mental-health-in-tech-survey) licensed under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)
The dataset is owned by [OSMI](https://osmihelp.org) and the contents of the website are also licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-sa/4.0/). It contains qualitative survey data conducted in the year 2019 about mental health in Tech and answers a range of questions about employers’ mental health policies along with candidates’ age, race, gender, and country of work and residence. 

This dataset contains all the necessary qualitative and quantitative information needed to analyze the problem at hand. Although the OSMI survey results are anonymized and do not contain PII, it still has sensitive demographic data(age, gender). The results of the analysis are purely to understand the factors affecting the mental health of people in tech and is not meant for disrespecting anyone.

All the raw data collected for the analysis is stored in [data/raw](./data/raw) folder.

### Unknowns and dependencies:

The Mental Health in Tech Survey data is skewed in the sense that the majority of survey participants are from the US and very few from low-income countries. The survey has answers from 1200 participants about 26 questions. The small sample size and skewness will create problems in making any strong claims on whether the region/country affects the mental health of people working there. It does not appear that the survey was administered to a representative sample and so, we won't be able to generalize the findings to a broader population. Also, as it is qualitative data, the analysis will heavily depend on the range of options for each categorical question. There might not be sufficient objectivity and also some bias in data collection steps. The variable, treatment (Have you sought treatment for a mental health condition?) may not be representative of the fact that whether individual suffers from a mental illness. 

### Research Questions

1. How does the frequency of mental health illness vary by age, gender?<br>
**Hypothesis**: Frequency of mental health illness is different for different demographic indicators.
 
2. Does family history of mental health illness impact the frequency of mental health illnesses?<br>
**Hypothesis**: The frequency of mental health illness is independent of family history of mental health.
 
3. Does attitude towards mental health impacts an individual’s decision to seek treatment for mental health condition?<br>
**Hypothesis**: The attitude towards mental health does not impact the individual’s decision to seek treatment for mental health condition.
 
4. What are the strongest predictors of mental health illness due to workplace environment? <br>
**Hypothesis**: A workplace that provides medical health benefits, awareness for care options to employees, safe environment to discuss the mental health issues with supervisor and peers contribute towards the better mental health of employees as opposed to a workplace that does not prioritize their employees’ health.

### Background

A related paper that measure the suicide tendencies in employees in tech industry based on the mental health illnesses and certain attitudes towars mental health in workplace [[1]](https://www.sas.com/content/dam/SAS/support/en/sas-global-forum-proceedings/2019/3966-2019.pdf) suggests that suicides rates in indicviduals are direct linked to mental health condictions are vary considerably in different age groups, gender, region. 
The study also suggests that companies which provide remote work, benefits and awareness around mental health have positive impact on employees’ mental health and in turn decrease in suicidal tendencies. 

The articles at [[2]](https://www.infoq.com/articles/mental-health-tech-workplace/) suggests that the major hindrance to mental wellness in a workplace is that mental illnesses are stigmatized and employees do not feel comfortable speaking up when they have a mental health issue due to fear to losing their promotion or job.

The OSMI [[3]](https://osmihelp.org/research) provides useful survey datasets from years 2014 
conducted every year which asks candidates about the mental health illness attitudes in their workplace(benefits, care options, consequence of informing employer about physical or mental health issures, awareness in employees related to employers policies and programmes around mental health, ability to take leaves of absense, etc.) along with demography data(age, gender, country). OSMI also provides guidelines for promote mental wellness in the workplace to eecitives and HR professionals based on studies conducted on the survey results.

Above research and resources are the basis for the research questions and hypothesis that I plan to answer in this analysis and it would be interesting to see what factors in the workplace contribute to improved mental health.  

### Methodology

#### Data cleaning and preprocessing 

Treating missing values:

- The data contains a lot of missing values in many columns. The default values of ‘NaN’ for string data type and default value of 0 for int data type will be used. 
- The column ‘Gender’ contains 49 distinct responses and will be changed to reflect just three gender types: male/female/trans(non-binary).
- To deal with missing values in the column ‘Age’, the median age will be used as the survey is mostly filled by people working in tech industry, once can assume that majority age-group of the participants is a safe choice of missing age. Also some values of age are too high or too low to be real numbers. Such values will be replaced by median age.
- For the columns with Yes/No inputs, the missing value will be replaced by ‘No/Don’t know’.

Encoding categorical data:

For each categorical data columns, we will apply label encoder to convert the inputs into classes. Further the age column needs to be normalised as it is an integer before applying any model to see the what are strongest predictors for an individual needing treatment.

#### Exploratory data analysis
 
To answer the research questions it would be helpful to plot some charts to see the counts of treatments/no treatments in various groups by gender, age, family history, work interference, etc. to see what is the probability of having a mental health condition in various groups and to make sense of data. A correlation matrix to see which features can be useful for analysis will also be helpful to plot. 

#### Feature selection 

Based on background and related work the following variables will be used to fit classification models to answer question 4, where the variable of interest is ‘Treatment’ i.e. whether the individual sought treatment for mental health condition implicit of the fact that individual has a mental health conditon:
'Age', 'Gender', 'family_history', 'benefits', 'care_options', 'anonymity', 'leave', 'work_interfere', ‘remote_work’, ‘self_employed’, ‘coworkers’, ‘supervisor’.
We will study to what degree each factor contributes to a mental health conditon.

#### Analysis plan for research questions:
To test **hypothesis 1**, we will measure the probability of having a mental health condition by country and see if there are significant differences by country. Then we will list the top 5, bottom 5 countries in terms of probability of having a mental health condition.
Also for US respondents, we will divide the states into 4 regions(West, South, Midwest, Northeast) and calculate the probability of having a mental health condition within these regions. 
We will also calculate the frequencies for mental illness amoung different age groups and genders and compare them on a bar plot. 

To test **hypothesis 2**, we will perform a chi-squared test of independence to see if the family history of mental health illness(family_history) and frequency of mental health illness(treatment) are dependent or whether the frequencies that we see in collected data are the once we would expect to get just by chance alone. 

Similar process will be used to test **hypothesis 3** where we will perform the chi-squared test of independence on the contingency table for variables mental_health_consequence and treatment.

For the **research question 4**, we will use logistic regression to model the predictors ('Age', 'Gender', 'family_history', 'benefits', 'care_options', 'anonymity', 'leave', 'work_interfere', ‘remote_work’, ‘self_employed’, ‘coworkers’, ‘supervisor’) on the dependent variable ‘Treatment’ and find out which of these variables strongly predict whether an individual has mental health  condition and therefore needs treatment.


### References

1) https://www.sas.com/content/dam/SAS/support/en/sas-global-forum-proceedings/2019/3966-2019.pdf

2) https://www.infoq.com/articles/mental-health-tech-workplace/

3) https://osmihelp.org/research

### License
This code is available under the [MIT License](./LICENSE).

The dataset [OSMI Mental Health In Tech Survey 2014](https://www.kaggle.com/osmi/mental-health-in-tech-survey) is available under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/).

### Terms of Use
By using the data and source code in this repository, you agree to their respective licenses. 


