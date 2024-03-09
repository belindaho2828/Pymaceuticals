# Purpose #
The purpose of this analysis of Pymaceuticals research data is to determine the effectiveness of their drug, Capomulin, on tumor development in cancer patients. To do so, they have conducted a study on 249 mice with squamous cell carcinoma over a 45 day observation period. The mice were given different drug treatments and the size of the tumor was measured at various timepoints. All mice had a starting tumor volume of 45mm.
# Tools #
Libraries used:
    Pandas
    Matplotlib
    Scipy
    Numpy
# Pymaceuticals Data Cleansing #
Two datasets consisting of observation results and mouse data were imported and read as CSV files. The two files were merged; value_count and .loc was performed on Mouse ID and Timepoint to identify duplicate records. The mouse and all its related records were dropped, resulting in 248 unique mouse IDs that we analyzed.

# Analysis #
The following tables and graphs were created to assist in this analysis:
## Summary Statisitcs (All Drugs) ##
In the summary statistics table listed by the tested Drug Regimen, we can see that the drugs Capomulin and Ramicane are the only two drugs where the mean tumor volumes decreased to 40.7mm and 40.2mm respectively from the original 45mm starting volume. Across the board of statistics (mean, median, variance, standard deviation, and standard error), Ramicane seems to perform slightly better since the tumor volumes reduced more than Capomulin when looking at the mean and median volumes over the timepoints. Tumor volumes on Ramicane have slightly less variability, with lower variance, standard deviation, and standard error values than Capomulin. 
## Bar Chart (All Drugs) ##
Pandas was used to create a data frame listing number of mice per Drug Regimen and bar charts plotted on the data using both Pandas and Pyplot. The data shows that there were more mice given then Capomulin and Ramicane than all other drug regimens.  There were 230 and 228 mice on Capomulin and Ramicane treatments respectively whereas other drugs had 148-188 mice. More investigation would be needed to see if this could be skewing the favorable results of Capomulin and Ramican drug regimens. More sample datapoints would provide a better representation of the population and less variability, which we saw of Capomulin and Ramican compared to the rest of the drug regimens. 
## Pie Chart (Male vs. Female) ##
Pandas was used to create a series that displayed number of mice in each sex and plotted as pie charts using both Pandas and Pyplot. The pie chart shows that the mice sample is pretty even between female and male sexes, which would be a good representation of overall population if the drugs were to be used on huamns.
## Boxplot (Capomulin, Ramicane, Infubinol, Ceftamin) ##
We want to focus on 4 drug regimens: Capomulin, Ramicane, Infubinol, and Ceftamin. To identify the final volume of the tumors under these 4 treatments, Pandas was used to find the max (latest) observed timepoint for each mouse and locate (.loc and for loop) the tumor volumes at that time point for each drug regimen. 

Pandas was then used to calculate the quartiles, which in turn was used to calculate the IQR and set the lower bound/higher bounds so we can determine the outliers of each drug. The only outlier found in tumor volumes was for Infubinol, which had 1 outlier of 36.83mm. 

Using Pyplot, we ploted a box and whiskers graph to show the much lower tumor masses of mice on Capomulin and Ramicane after treatment vs. mice who were on Infubinol and Ceftamin treatments. In this view where we only focus on the data for the last timepoint, the tumor volumes for Capomulin have less variability than the tumor volumes for Ramicane whereas it was the opposite when looking at all timepoints. 
## Line, Scatter, and Regression (Capomulin Only) ##
### Line ###
A line graph was plotted using Pandas to show the tumor volume decrease over the 45 day timepoint during the Capomulin drug regiment treatment for mouse l509. The line shows an initial increase of tumor volume for the first 20 days of treatment followed by a drastic decrease for 15 days after the initial increase (with a short increase before day 30) and another uptick at around day 35 of the treatment. This indicates that the drug may have a timing component of when it would affect the tumor development. More data would be needed to see if the medication is time released. 

### Scatter and Regression ###
Pyplot was used to plot a scatter plot and regression line using linregress function from scipy library between mcie weight and final avg. tumor volume of mice on Capomulin. The datapoints on the scatter plot is tightly clustered around the regression line and the linregress function returned a coefficient of 0.84, which indicates a high positive correlation between the weight of the mouse and average tumor volume at the final observed timepoint. This could mean that Capomulin is less effective on heavier mice. 

## Conclusion ##
Capomulin and Ramicane drug treatments both drastically decrease tumor volumes over the observed timepoints with Capomulin having lower variability at the last timepoint. THese two drug treatments performed the best out of all observed treatments. A few considerations for future research: 
- observing equal amounts of mice for all drugs since the larger sample sizes for Capomulin and Ramicane could have skewed the results.
- more information about time release of each drug regimen to decrease bias around which timepoint we select data to compare the drug regimen. As we saw in the line graph for 1 mouse under Capomulin treatment, there were time intervals at which the drug was decreasing the tumor volume and when the volume seemed to increase. We should take care not to compare drug regimens at the same timepoints if their time release are at different points.
- weight of the mice had high correlation to the tumor volume. As such, more research should be done on the impact of weight and drug effectiveness like sampling more mice of the same weight group and conducting further tests of the desired drug treatment.

# Acknowledgements #
Besides the starter code, all other code was original. I used chatGPT and stack overflow for understanding general concepts and debugging. I received help from the TAs on dropping duplicate mouse data and the for loop used in the boxplot exercise.
