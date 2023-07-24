ISSUES
There are several issues with teh data and code that need to be adresses:
From README:
1. Addition of Classes: 
a. In line 520 Ð 526, the participants in the classes are added to respective vectors. This is hard-coded for class 1-4. When selecting more or less classes in the final model, they need to be added/ removed by hand.
b. In function class_and_class_name(), the four classes and their respective names are hard-coded. When selecting more or less classes and/ or renaming the classes, they need to be changed.
2. Computation of Age: In the creation of the data_demographic dataframe, the first observation that they filled in HBSC questionnaire is used to decide the age and education level. For 1 person, the age value and the HBSC questionnaire values that were not missing where split, thus this one age value is added by hand. Can happen more often when using different participants.
3. Correlation Table: Correlation is computed by using one observation per person, and this being the closest to the onset of the COVID-19. The correlation was also computed between factors of different questionnaires and they could be filled in at a totally different time point (one year apart). It might be beter to retrieve observations that are the closest in time for a more reliable correlation.
Other:
4. Cantril Values Discrepancy: In some instances, participants completed a Cantril value twice on the same day in different questionnaires had a low correlation for values that should measure the exact same construct. Need to be looked into why, and maybe only use the ones from the same questionnaire.
5. GMM Performance: The GMM models have a low number of iterations (maxiter = 100). This is not ideal for performance. Note that models with a high number of iterations (maxiter > 5000) can take several hours to run.
6. Statistical Tests: The ANOVA tests are for >2 latent classes. This should be T-tests when comparing two classes.
