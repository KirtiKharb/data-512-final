# Impact of the workplace environment and happiness index of a region on Mental Health

### Motivation/Problem statement:
Mental health has become a serious concern in the 21st century. As people in technical jobs lead a sedentary lifestyle and have very few social engagements outside their workplace, It is important to study the factors in a workplace that affect an individual’s mental health. I want to know how employers can take measures to promote their employee’s mental health and spread awareness to address this growing concern. Aside from company policies with regard to health, leaves, insurance, etc., the ability to comfortably communicate health problems with colleagues and supervisors can have a serious impact on an employee’s mental health. I also want to study the impact of the general happiness index of the country where an individual works on his/her mental health. 

### Datasets:
For this project, I will use two datasets that are publicly available on [Kaggle](https://www.kaggle.com/).
- [OSMI Mental Health In Tech Survey 2019](https://www.kaggle.com/osmihelp/osmi-mental-health-in-tech-survey-2019) licensed under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)
The dataset is owned by [OSMI](https://osmihelp.org) and the contents of the website are also licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-sa/4.0/). It contains qualitative survey data conducted in the year 2019 about mental health in Tech and answers a range of questions about employers’ mental health policies along with candidates’ age, race, gender, and country of work and residence. 
- [World Happiness Report]( https://www.kaggle.com/unsdsn/world-happiness) licensed under [CC0: Public Domain](https://creativecommons.org/publicdomain/zero/1.0/)
The dataset is owned by [Sustainable Development Solutions Network](https://www.unsdsn.org/). It contains the happiness scores for 156 countries from the years 2015-2019 along with GDP per capita, social support, healthy life expectancy, freedom to make life choices, generosity, and perceptions of corruption.

These two datasets will help in providing all the necessary qualitative and quantitative information needed to analyze the problem at hand. Although the OSMI survey results are anonymized and do not contain PII, it still has sensitive demographic data(age, gender, race). The results of the analysis are purely to understand the factors affecting the mental health of people in tech and is not meant for disrespecting anyone.

All the raw data collected for the analysis is stored in [data/raw](./data/raw) folder.

### Unknowns and dependencies:

The Mental Health in Tech Survey data is skewed in the sense that the majority of survey participants work in the US and very few in low-income countries. The survey has answers from 352 participants about 82 questions. The small sample size and skewness will create problems in making any strong claims on whether the happiness score of a country affects the mental health of people working there. Also, as it is qualitative data, the analysis will heavily depend on the range of options for each categorical question. There might not be sufficient objectivity and also some bias in data collection steps. 

### License
This code is available under the [MIT License](./LICENSE).

The dataset [OSMI Mental Health In Tech Survey 2019](https://www.kaggle.com/osmihelp/osmi-mental-health-in-tech-survey-2019) is available under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/).

The dataset [World Happiness Report]( https://www.kaggle.com/unsdsn/world-happiness) is available under [CC0: Public Domain](https://creativecommons.org/publicdomain/zero/1.0/).

### Terms of Use
By using the data and source code in this repository, you agree to their respective licenses. 


