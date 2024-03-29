# Project-1---Group-9

## Overview
Video games have been a popular hobby since the early 1970s, ranging from classic arcade consoles to portable handheld devices and computers. Many people all over the world enjoy the plethora of possibilities that video games offer: they can play for fun or professionally, alone or with others, simple games like Tetris or complex role playing games (RPGs) like League of Legends. While this pop culture phenomenon has had a significant impact on society in many ways, how does it affect mental health, and subsequently, people's lives?

In this project, our group decided to investigate how video games impact our mental health and lives. We found this dataset via Kaggle that included the recorded responses of over 13,000 players worldwide. The original survey was conducted in 2017 by Marian Sauter and Dejan Draschkow, and includes data relating to generalized anxiety disorder (GAD), satisfaction with life (SWL), gaming platform, reasons for playing, playstyle (alone or with others), hours played per week, employment status, education status, country of residence, social phobia inventory (SPIN), and demographics suchs as age and gender identification. We considered the available information and narrowed down the dataset to answer these four questions:

1. How do gamers that play professionally compare to gamers that play for fun?
2. Do professional gamers have a better satisfaction with life (SWL) score than casual gamers?
3. Are those who play alone more anxious than those who play socially?
4. US Residents versus European Residents: who spends more time gaming per week, and how does it compare to their SWL score?

Our goal was to analyze this data and answer our questions using skills learned such as Python, Jupyter Notebook, Pandas, and Matplotlib.


------------

## Analysis
### Data Cleaning Process
The cleaning process was started by importing the data via CSV file. We found that there were some issues with foreign characters popping up, as well as some column values being shifted by some responses with commas in them (i.e. the commas did not play well with the CSV format). To overcome this issue, we opened the CSV file in an Excel workbook and edited out extraneous commas and characters.

Once the CSV was cleaned up in Excel and re-read into our Jupyter Notebook, we needed to reduce the number of columns while maintaining enough data for each of us to answer our research questions. Out of 55 total columns, we elected to keep the Survey Number (S. No), Game, Platform, Hours (played per week), Earnings, Why Play, Gender, Age, Work (i.e. employment status), Degree (highest level of education received), Residence (by country), Playstyle (alone versus socially), Generalized Anxiety Disorder Score Total (GAD_T), Satisfaction with Life Score Total (SWL_T), and Social Phobia Inventory Score Total (SPIN_T). This resulted in a dataframe that is 13,464 rows by 15 columns, and was much more suited to our needs.

### 1. How do people who play for money compare to people who play for fun?
#### Analysis by Aliyu Muraina
The deduction from this part of the analysis is that there are more people playing video games for fun than for competition: 5289 versus 2091. People who play primarily for fun may have lower anxiety levels on average compared to those playing professionally for money. Playing as a hobby rather than for income may be less stressful.
There are 2734 people with employment that play just for fun, compared to the 1390 people that are unemployed. The analysis also showed that people play to spend time with friends and family.


### 2. Do professional players have a better Satisfaction with Life (SWL) score than casual players?
#### Analysis by Andrew Arjune
In this section, it was found that the percentage of players who game solely for fun was 92%, i.e. those not playing to make a living generally have a higher SWL score than competitive or professional gamers, averaging 1.5 points higher. This was in line with what our team hypothesized, especially given how skewed the dataset seemed to be. Of the players asked, 84% were playing League of Legends, an exclusively online game with little to no single player options. This presents a fairly substantial sample of bias, as casual players are more likely to decompress while gaming, while professional players are more likely to be focused on gaming performance, mechanics, and other aspects, making them less likely to just sit back and enjoy their gaming experience.


### 3. Are those who play alone more anxious than those who play socially?
#### Analysis by Anna Bitzer
The results of this data found that while all styles of playing video games were associated with similar average GAD scores, the total average GAD score of players who played alone was higher than players that played multiplayer. The mean GAD scores of players that played offline multiplayer, with real life friends (mean GAD = 4.21) and online multiplayer, with real life friends (mean GAD = 4.77) were below the overall population mean (GAD = 5.22), suggesting that less anxious players may be more comfortable playing with people they know in real life. The remaining playstyles multiplayer-online-with online acquaintances or teammates, multiplayer-online-with strangers and single player had mean GAD scores above the population mean, of 5.47, 5.57 and 5.80 respectively.

A Welch's t-test was performed to compare the group with the lowest mean GAD score of 4.21, gamers that played offline multiplayer, against the group with the highest mean GAD score of 5.80, gamers that played single player. It was found that there is a slightly significant difference between the two groups, with a p-value of 0.03. It should be noted that these two groups were by far the smallest of the playstyles analyzed - 5.8% of the population played single player, and only 0.4% of the population played offline multiplayer.

The GAD data was not normally distributed, and was instead right skewed, with the median less than the mean for all playstyle categories. Results for all playstyles ranged from 0-21 (with the exception of the multiplayer-offline-friends in the same room group, which had a range of 0-20). There were a significant amount of high outliers for each group, bewteen 2-8% of data points were outside of the range of 1.5 times the IQR for each group.

There were some limitations to this dataset. The majority of respondents to this dataset listed League of Legends as the primary video game that they played. As this is a multiplayer game, the distribution of the data is skewed away from single player gamers. A dataset with a more even breakdown of single player versus multiplayer gamers would allow a more accurate view of anxiety levels of those who game alone versus those who game with either online or real life friends.

Sources used: https://stackoverflow.com/questions/26700598/matplotlib-showing-x-tick-labels-overlapping Bootcampspot: Xpert Learning Assistant (used for outlier section, and for help formatting boxplot)


### 4. US Residents vs European Residents: who spends more time gaming, and how does it compare to their Satisfaction with Life (SWL) score?
#### Analysis by Amy Dohlin
The total of USA and European players makes up the vast majority of the population of the dataset. This number was found by pulling the country names, and manually filtering out non-USA and non-European countries/regions. If time permitted, it would be more efficient, accurate, and beneficial to pull the region data from Geoapify API and compare data from all continents.

The original hypothesis was that US residents would spend more time gaming and have a lower SWL score than their European counterparts. The data suggests that on average, gamers in the USA spend fewer hours playing video games per week, and have a slightly better satisfaction with life score than European gamers. These results may also be skewed due to more European players taking the survey than US players.

Histograms were created to show the frequencies of SWL scores (USA versus Europe) and hours played per week. Overall, these charts show that European players reported SWL scores that were spiking in the 15 to 25 range (out of a possible score of 42, with 0 being unsatisfied with life and 42 being most satisfied with life), whereas US players have a more even distribution of scores in the same range. Both regions reported identical average hours played per week (22.31 hours for Europe, 20.45 hours for US), but Europe had a maximum of 140 hours per week and the US had a maximum of 105 hours per week.

A t-test was performed on the SWL scores from the US and Europe, and garnered results of t-statistic=4.498068691660252, pvalue=6.93805963055848e-06. The large t-statistic and low p-value indicate a significant difference in the SWL scores between the US and Europe. If the numbers of players distributed between the US and Europe were more even, the result might be less significant. It would be interesting to see what the result would be with all countries in the study represented, it would likely have an even larger difference due to the small population sizes from other countries.

This question could be further analyzed with other factors taken into account, such as employment status, earnings, age, gender, play style, etc. Other limitations to this dataset could be that the total number of participants who took this survey represent only a fraction of gamers worldwide, and could be even more limited depending on where gamers found the survey and how long it was available.

### Sample of Bias Discussion: was this data geared more towards collaborative RPGs versus other games?



------------

## Summary
Based on the data retrieved, video games do have a significant impact on our mental health. Question 1 reveals that more gamers play for fun than to make a living, and may be less anxious because of this. Along this same vein, question 2 correlates a higher SWL score for casual gamers, and a lower SWL score for professionals. Question 3 shows that when gamers play with friends in person (offline) they're less likely to be anxious than if they were playing alone, and could be construed that more personal social interaction between gamers could make gaming more enjoyable and relaxing. The data in question 4 comparing the USA and Europe shows a correlation between more hours spent playing and a lower SWL score, suggesting that more balance between video games and off-screen activities (perhaps with friends) could elevate a gamer's general life experience. Overall, we can conclude that playing video games casually and for relaxation will cause less mental distress than playing video games for a living.


-----------

## Sources
Dataset: https://www.kaggle.com/datasets/divyansh22/online-gaming-anxiety-data?select=GamingStudy_data.csv
Original Survey: https://osf.io/vyhttpsr5f
Xpert Learning Assistant via Boot Camp Spot
