# The Opioid Hackathon 2019 Track 5
The Hackathon is to present solutions to prevent increasing opioid overdose deaths in United States.
It approaches solving problem in software application way or data science/ AI.
The focus is on California, Orange county specifically, but to expand it's solution nationwide.

[More details about the Hackathon](https://www.theopioidhackathon.com/)  
[Photos of Winners](https://twitter.com/predictech/status/1195162633319534592/photo/1)

## Track 5
> Real-time/prediction models and visualization tools to assist Orange County Public Health and UCI Health to prevent addiction and overdose. 

## Programmers: 
- [Jungin Hong](https://www.linkedin.com/in/junginh/) 
- [Lanting Li](https://www.linkedin.com/in/lanting-li-a15883198/)

## Our solution
Use tweets, 7 economical features, 8 possible targets  
Provide prediction model using Scikit-learn library  

### Data
**7 economical features**  
1. CANQGSP
2. CAODIV
3. CAOTOT
4. CASTHPI All-Transactions House Price Index for California
5. CAWHEA Health Care and Social Assistance Wages and Salaries in California
6. CAWMIN
7. UNEMPLOYCA  

**8 possible targets**  
1. Prescriptions Rate (annualized quarterly rate)
2. Prescriptions Count
3. Hospitalizations Rate (annualized quarterly rate)
4. Hospitalizations Count
5. ED Visits Rate (annualized quarterly rate)
6. ED Visits Count
7. Deaths Rate (annualized quarterly rate)
8. Deaths Count

**Tweets**  

### Preprocessing.ipynb
1. Tweets data(JSON) from Nov 2015 to March 2019
2. Split tweet contents into words and store frequency to dictionary (remove tags/emojis/links)
3. return word frequency spreadsheet: Matrix.csv

### Economic.ipynb 
- All of our models have high RMSE, but due to very small data size (see 0.)
0. From Economic_Indicators.csv file(data, see link below) 2006 Q1 to 2019 Q2 (around 50 data)
1. First, find correlation of 7 economical features & 8 target values  
   ![7Features8targets](https://user-images.githubusercontent.com/45378526/114261026-3473ea00-9a13-11eb-97f0-f2d5681daf32.PNG)  
2. plot 7*8 graphs  
  - CAWHEA & ED Visits Rate: linear regression  
  ![ER_CAWHEA](https://user-images.githubusercontent.com/45378526/114264757-b66e0e00-9a27-11eb-88c4-21f7d4eba600.PNG)  
  ![ER_CAWHEA_result](https://user-images.githubusercontent.com/45378526/114264781-db628100-9a27-11eb-9458-1cee3db8780f.PNG)  
  - CASTHPI & Hospitalizations Rate: linear regression similarly  
3. Random forest regressor tested on Hospitalization rate with 7 features, extracted feature_importances_  
   CASTHPI has .5756 feature importance (highest relevance)  
   ![randomforest_result](https://user-images.githubusercontent.com/45378526/114269585-f393c980-9a42-11eb-92c8-28d121f6fe0e.PNG)  
4. Lasso regression has high R^2 and high RMSE
   
### Words.ipynb
Randomly select 10,000 tweets in U.S. area  
select 50 frequent words from Matrix.csv
graph words against death data

### Other suggestions
In future application: the tweets can be updated and fed into the algorithm to strenghten \
Further tweets contains information about the area \

### References
*Tweets are from Professor _____ at UCI.* \

Economic data from:  
- https://fred.stlouisfed.org/series/CANQGSP  
- https://fred.stlouisfed.org/series/CAODIV  
- https://fred.stlouisfed.org/series/CAOTOT  
- https://fred.stlouisfed.org/series/CASTHPI  
- https://fred.stlouisfed.org/series/CAWHEA  
- https://fred.stlouisfed.org/series/CAMIN  
- https://fred.stlouisfed.org/series/CAWTOT  
- https://fred.stlouisfed.org/series/UNEMPLOYCA

Any Opioid-Related Overdose:
- Death, ED Visits, Hospitalizations, Prescriptions
- https://skylab.cdph.ca.gov/ODdash/
