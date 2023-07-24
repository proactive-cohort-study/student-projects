# README

This README files provides an overview of the corresponding R script (ÒThesis_Marjolein_Rietdijk_4405668.RmdÓ) used for identifying latent classes with Growth Mixture Modelling (GMM) and their corresponding differences in resilience factors (as measured by the HBSC items Òsupport at homeÓ and Òsupport from friendsÓ, the READ domains Òpersonal competenceÓ, Òsocial competenceÓ, Òstructured styleÓ, Òsocial supportÓ and Òfamily cohesionÓ and the PedsQL domains Òphysical functioningÓ, Òemotional functioningÓ, Òsocial functioningÓ and Òschool functioningÓ among children of the PROactive cohort. The script performs various data processing steps, statistical analysis and generates visualizations.
Database and files
The database used for analysis is a SPSS-file in .sav format, which can be found at the following:
(ÒL:/Onderzoek/SP_16-707_PROactive_II/E_ResearchData/1_Students-and-researchers/2023_Marjolein_ADS-thesis_UU/01_moederbestanden-niet-analyseren/23-5-23_Database_Jeroen_Marjolein-FINALÓ)
An additional file was added for the stringency index:
(ÒL:/Onderzoek/SP_16-707_PROactive_II/E_ResearchData/1_Students-and-researchers/2023_Marjolein_ADS-thesis_UU/06_documenten/Aangeleverd-door-Anne/Stringency_index/202305_export_owid-covid-dataÓ)
Important functions
create_data(): creates a new dataframe where for analysis. It adds the PatientID_pseudo and QuestionnaireStart automatically, and merges the QuestionnaireStart and InvulDatum columns, so that the QuestionnaireStart is preferred, but when missing it is filled in with an InvulDatum value. It also adds a new column Òbefore_after_covidÓ that contains a B if the observation was before the start of COVID, and an A if the observation was after the start of COVID. Also removes observations that donÕt contain values for the columns that are added (thus not the QuestionnaireStart and PatientID_pseudo)
ceate_data_B1(): creates a new dataframe where for analysis of resilience factors. Input should be a dataframe that is created by create_data(). Removes rows that are empty (except for PatientID_pseudo and QuestionnaireStart). Only keeps the first observation for each participant if observation = ÒfirstÓ, and the nearest but before COVID if observation = ÒlastÓ (default).
Data Processing Steps
Cantril values are that are filled in in the HBSC and COVID-questionnaire are averaged and taken as one observation. 
Partipants that did not fill in Cantril-ladder before and after start of COVID are removed. 
A time variable is added where the dates are changed into time (in days), where time = 1 is the earliest observation of the participating participants. This is done to ensure GMM performance.
The script utilizes the lcmm package in R to perform GMM. For detailed instructions on using the lcmm package and interpreting the results, refor to this resource: https://psyarxiv.com/m58wx/
The script provides code to perform GMM with random slope and fixed intercept, random intercept and fixed slope, and random slope and random intercept. The different classes of all models are visualized. By changing variable final_model to the preferred model, analysis will with the preferred classes (see ISSUES.txt).
Resilience Factors
All resilience factors used are nearest to the onset of COVID. These are selected by create_data. 
Statistical Analysis and Visualization
Because of the violations of assumptions, the classes are compared with robust ANOVA and Dunn-Bonferroni tests for each resilience factor.
The differences are visualized with boxplots.
Other
Demographic variables age and education are measured at the first time point children filled in HBSC-questionnaire (see ISSUES.txt).
Correlation between all variables (Life satisfaction and resilience factors) are computed with one observation per person, closets to the onset of COVID-19 (see ISSUES.txt).
CronbachÕs alphas are computed for the resilience factors, using the observations that are used in the analysis, thus the closest to the onset of the COVID-19 pandemic.
Note: Please ensure that all required packages are installed before running the script.
