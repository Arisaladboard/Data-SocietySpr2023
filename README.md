# Data-SocietySpr2023







Mortgage - All A Loan

Cynthia Nguyen, Ari Salenpour, Victoria Thornton, Chenyang Wei
DAT 4500: Data & Society
Department of Mathematics
Seattle Pacific University
Dr. Brian Gill
June 8, 2023




Mortgage - All A Loan
Abstract
This report aims to understand foreclosure rates in U.S. counties based on 2019 data likely used to influence the allocation of money for the Homeowner Assistance Fund from Urban Data Catalog. Based on the variables dealing with mortgage shares and area median income for every county from the Urban Data Catalog dataset and literature on foreclosure rates, other variables were pulled from the Bureau of Economic Analysis, the Bureau of Labor Statistics, and the Census API to get a fuller picture on macroeconomic activity and demographics across all the counties. We attempted to build linear models that reflect predicted foreclosures given by Urban Data Catalog and identify counties most at risk for spikes in foreclosure rates based on the data we had. Urban Data Catalog provided no method on how they calculated their predicted foreclosure rates other than that they used housing market and economic measures. After joining all our data, we found that Urban Data Catalog likely did not examine demographic information other than race such as marital status shares and education level shares. Despite the discrepancies from Urban Data Catalog, we attempted to still get insights from county-level homeowner data.


Introduction
The Homeowner Assistance Fund (HAF) was created in 2021 by the American Rescue Plan Act, also known as the COVID-19 Stimulus Package. $1.9 trillion was made available in this economic stimulus bill which was needed due to the coronavirus pandemic’s impact on the American economy. The HAF received $9.961 billion to support homeowners facing financial hardship associated with COVID-19. Many Americans lost their jobs or were furloughed during the pandemic, losing their income stream and ability to cover their costs of living. Therefore, federal funds were set aside for homeowners to act as an assistance with mortgage payments, homeowners insurance, utility payments, and more. HAF money was given to U.S. states, U.S. territories, and Indigenous tribes. Through 2022, HAF-funded programs have assisted over 230,000 homeowners.

According to the bill, at least 60 percent of funds “shall be used for qualified expenses that assist homeowners having incomes equal to or less than 100 percent of the area median income for their household size or equal to or less than 100 percent of the median income for the United States, … whichever is greater.” The remaining funds (up to 40 percent) shall be prioritized to socially disadvantaged individuals. Qualified uses of HAF money include mortgage payment assistance, mortgage reinstatement, principal reduction, interest rate reductions, utilities, internet, homeowner’s insurance, homeowner’s association fees, and “any other assistance to promote housing stability for homeowners, including preventing mortgage delinquency, default, foreclosure, post-foreclosure eviction of a homeowner, or the loss of utility or home energy services.”

This led us to our first and primary research question: what are the most significant factors that can be used to predict whether a county’s foreclosure rate will increase? It is clear that the purpose of the HAF funding is to provide relief to homeowners facing financial hardship so as to prevent foreclosures. Through an analysis of our dataset, we sought to identify factors that have predictive significance for foreclosures at the county level.

Our second research question had to do with identifying at-risk counties. We asked, “which counties are most at-risk to spikes in foreclosure rates?” By identifying at-risk counties, the federal HAF can more appropriately target its funding to those who are most at risk of foreclosure. The American Rescue Plan Act lays out some guiding policies for the distribution of funds. However, the approval process and transaction of funds is carried out by each state, territory, or tribe. We believe states with counties that are more at risk should have access to greater financial resources so as to best help those in the most need. Please read more about our findings and analysis in the Results section.

For context, all U.S. states, Washington D.C., and Puerto Rico each received a minimum of $50 million. For states that received more than this amount, their funding increased by a pro rata method based on homeowner need.** $30 million was split between Guam, American Samoa, the U.S. Virgin Islands, and the Northern Mariana Islands based on population. The bill claims the Department of Hawaiian Homelands and various Indian tribes received funding, though it was unclear the specific amounts earmarked for these groups. $42.6 million was designated as overhead funding for the purpose of running the HAF organization. Please see the resources in the appendices for more information on how much funding each state received as well as the area median income charts. It should be noted that funds are given to each state’s housing assistance program and it is up to the states to properly distribute the money to those in need. 

The American Rescue Plan Act was passed March 11, 2021 and the Urban Data Catalog’s “Homeowner Assistance Fund County-Level Targeting Data” was published September 23, 2021. In these six months, the Homeowner Assistance Fund compiled this dataset to determine who would receive--or qualify for--assistance. The bill does lay out some clear qualifiers for federal aid, such as a homeowner’s income level. However, the bill’s definition is too broad. Therefore, HAF assembled this dataset to identify homeowners who were most vulnerable to financial hardship by COVID-19. This dataset was used to conclude how much funding each state would receive. Needs a better concluding sentence for the introduction.

** Homeowner need is determined based on the average number of unemployed individuals over a period of 3-12 months AND the total number of mortgagers with mortgage payments more than 30 days past due or mortgages in foreclosure.


Methods
Our original dataset was the Homeowner Assistance Fund County-Level Targeting Data from the Urban Institute’s Urban Data Catalog (Urban Catalog). Because this was county-level data, we had 3,141 records and 23 variables. Please see Table 1 below for a description of all the variables included in this dataset. We determined that more data was needed to help us draw more accurate conclusions regarding our objectives. Therefore, we found datasets that included variables that were missing from our original dataset yet could be a contributing factor to our objectives. We found data for population, economic status, education levels, and marital status across all U.S. counties.

After digging more into how this data was collected, it became clear that the U.S. Census Bureau is the main source for most of the data collection. The Census Bureau sends field representatives to randomly selected households to gather data. For this particular study in 2019, data was collected on 3.5 million households. The Census API data is intended to be representative of the entire U.S. population. The Urban Catalog dataset claims to be sourced from the American Community Survey (ACS). The Census Bureau conducted the ACS so we can be sure the methods the Census Bureau used were consistent between the ACS and Census API sources.

The Urban Catalog and Census API datasets were rooted in the survey that the Census Bureau conducted; this means the sampling methods were the same. We also used marital status, education, and monthly median income from the same 2019 Census API data. The sampling was the same, just they broke down the data into more specific subsets. We also used data from the Bureau of Economic Analysis and Bureau of Labor Statistics. The data coming from the Bureau of Economic Analysis comes from a variety of different agencies, the Census Bureau is one of the agencies they rely on for data. The Bureau of Labor Statistics collects their data from the Census Bureau, so their sampling methods are the same and were covered earlier. 
To find out the elements that significantly affect the housing assistance funding, it is decided that using datasets from Urban Institute Data Catalog, Bureau of Economic Analysis, Bureau of Labor Statistics and Census API to figure out the influence from Income, race, local real GDP, mortgage, education level, employment and martial status.
For the dataset of HAF, the table was combined based on the variables of FIPS code, county name, state initials, with the “join()” function from R programme, and it was joined with share of mortgage, income situation, predicted rate of foreclosure, homeowner share based on race, real GDP, share of cost burden and severe burden, martial status, unemployment rate by counties. The variable used are listed below:

Table 1
HAF Data Dictionary from Urban Institute Data Catalog:
Variable name
Defination
State
State name
County
County Name
Homeowners less 100 AMI
Number of homeowners earning less than 100 percent of area-median-income
Homeowners less 150 AMI
Number of homeowners earning less than 150 percent of area-median-income
Mortgages less 100 AMI
Number of homeowners with an outstanding mortgage earning less than 100 percent of area-median-income
Mortgages less 150 AMI
Number of homeowners with an outstanding mortgage earning less than 150 percent of area-median-income
Total Homeowners 
Total number of homeowners 
Total Mortgages
Total number of homeowners with an outstanding mortgage
Homeowners 100to150 AMI Non-white
Number of non-white homeowners earning between 100 and 150 of area-median-income
Homeowners 100to150 AMI white
Number of white homeowners earning between 100 and 150 of area-median-income
Predicted Foreclosure Rate
Urban's predicted foreclosure rate metric 
Black Homeowner Share
Share of homeowners that are Black
Non-Hispanic white Homeowner Share
Share of homeowners that are non-Hispanic white
Asian Homeowner Share
Share of homeowners that are Asian
Hispanic Homeowner Share
Share of homeowners that are Hispanic
Other Homeowner Share
Share of homeowners other race/ethnicity 
Mortgage Share
Share of total homeowners with an outstanding mortgage (total mortgages / total homeowners) 
Median Owner Cost
Median monthly homeownership costs
Median Owner-Cost-to-Income Ratio
Median monthly ownership cost to income ratio
Cost Burdened Homeowners (with mortgage)
Number of cost-burdened homeowners with a mortgage (spending 30 percent or more of annual income on housing costs)
Share Cost Burdened 
Share of homeowners with a mortgage who are cost-burdened 
Share Severe Cost Burdened 
Share of homeowners with a mortgage who are severely cost-burdened (spending 50 percent or more of annual income on housing costs)
Puma Estimate Flag
Indicator for when population estimates were calculated from PUMA level data using a crosswalk because the county did not meet the 100,000-person population disclosure threshold. Estimates that are sourced from 2019 5-year American Community Survey Micro Data and Urban Institute Calculations will differ slightly from census summary estimates (where summaries are available). 


Table 2
Bureau of Economic Analysis Data Dictionary
Variable name
Definition
RGDP 2012
The real GDP for each county in 2012
State
State name
County
County Name

 
Table 3
Bureau of Labor Statistics Data Dictionary
Variable name
Definition
Labor force
The number of people who is at working age in each county
Employment
The number of people who has a stable job in each county
Unemployment
The number of people who does not have a job in each county
Rate of unemployment
The rate of people who does not have a job in each county
State
State name
County
County Name
FIPS
Federal Information Processing System (FIPS) Codes for States and Counties

 
Table 4
Census API Data Dictionary 
Variable name
Definition
FIPS
Federal Information Processing System (FIPS) Codes for States and Counties
County
County Name
Share of grad or prof
The share of people who received a post-graduate degree in this county
Share of bachelor
The share of people who received a bachelor degree in this county
Share of some col or assoc
The share of people who received a associate degree or equivalent in this county
Share of HS
The share of people who received a high school degree or equivalent in this county
Share of less HS
The share of people who did not receive a high school degree in this county
Share of none married
The share of people who is single in this county
Share of married
The share of people who is married in this county
Share of divorced
The share of people whose was married but broke up in this county
Share of separated
The share of people whose marriage couple is not live with them in this county
Share of widowed
The share of people whose marriage couple is dead in this county
Share of other marriage situation
The share of people who has other married situation in this county

 

Table 5
Variables Mutated
Variable name
Definition
Formula
Rate for homeowners without outstanding mortgages
The rate for people who completely own a house in a county
(Total homeowner-Total mortgage)/Total homeowner
Cost-to-Income Ratio
Median monthly homeowner costs to median income (ACS)
Median monthly homeowner costs/Median Income



The hypothesis test was used to find out the relationship between the foreclosure rate and these elements. The null hypothesis (H0) is set as there is no significant relationship between foreclosure rate and these elements while the alternative hypothesis (HA) is there is significant relationship between foreclosure rate and these elements. If the P-value is lower than 0.05, this means we have evidence to reject the null hypothesis. Rejecting the null hypothesis in this context means that the predictor we used has a significant correlation to foreclosure rate.
With the help of “summarize()” function in R Program, the coefficient, p-value, R-square value can be collected for each hypothesis test between foreclosure rate and race, cost burden, unemployment rate, martial rate and real GDP. (See table 7 in Results part for coding sample)


Results
 
  	Based on the originally imported Urban Data Catalog dataset, several counties were missing their median monthly homeowner cost-to-income ratio and a few were missing their share of cost-burdened homeowners. Figure 1 shows the proportion of homeowners who spend at least 30% of their income on outstanding mortgage payments for each county. The county with the most cost-burdened homeowners is Fall River County in South Dakota with over 70% of homeowners being cost-burdened. Generally looking at Figure 1, a majority of the coasts are reading more red than yellow, having higher shares of cost-burdened homeowners. Considering the magnitude of cost-burdened is based on income, we made Figure 2 to see if there were match-ups with the median monthly homeowner cost-to-income ratio using American Community Survey data from the Census API.


Fig. 1. Map Visualization of Cost-Burdened Counties using Urban Data Catalog’s data


Urban Data Catalog’s data only had median monthly homeowner costs with many missing elements and no explicit median income of each county, so ACS data was used to recalculate the ratio. To check for large discrepancies between the median monthly homeowner cost from Urban Data Catalog and the ACS, we ran a correlation test between both their median monthly homeowner cost and got back a correlation of approximately 0.87. The correlation being only about 0.87 could have been due to the missing data from Urban Data Catalog’s side, but Urban Data Catalog’s dataset’s webpage points towards ACS being the primary source they are pulling data from. Moving past the discrepancies, Figure 2 shows many counties having high median monthly homeowner cost-to-income ratios across all states. While California in Figure 1 has most counties coming with about 30% to 40% of their homeowners being cost-burdened, Figure 2 shows much deeper shades of red around the coast indicating severe cost-burdenedness with such high cost-to-income ratios.


Fig. 2. Map Visualization of Monthly Cost-to-Income Ratio using Census API data


	In general, it can be found out that the counties with higher cost burden are almost be covered by the highest median monthly cost-to-income ratio. Also, some states like California, Florida, New York, New Jersey and Massachusetts can be more obvious to find out that there is a potential pattern that the higher the cost-to-income ratio, the more likely for this county to be in cost burden. The cost-to-income ratio does factor in homeowners without outstanding mortgages as well since it accounts any costs going towards homes as well as mortgage payments if they did have outstanding mortgages.
	For robustness, Figure 3 attempts to relate income with share of cost burden using only the dataset from Urban Data Catalog. Area median income is calculated using Urban Data Catalog’s median income-to-cost ratio, which results in some counties missing from the plot. From what is not missing, most counties fall between having about 15% to 30% of their homeowners being cost-burdened by their mortgage with median monthly incomes of about $3,500 to $6,000. Counties that are likely to have higher foreclosure rates would be ones that are closer to the top left corner of the plot, since that would signify a county with many residents with relatively lower income and a majority being cost-burdened.


Fig. 3. Area Median Income & Share of Cost Burden using Urban Data Catalog’s data


	To perform hypothesis tests on factors that may affect the foreclosure rates. The possible aspects are race, educational level, unemployment, marital rates, cost burden ratio, median owner cost and local Real GDP. All variables are proportions of their respective levels within each county. Table 6 is a series of simple linear regressions performed to relate the mentioned variables to the predicted foreclosure rates done by Urban Data Catalog. Figure 4 was created using the step() function in R to get the subset of variables out of the macroeconomic variables, demographic variables, and cost-to-income ratio variable with the highest R-squared value. The result of the hypothesis testing is listed as below:

Table 6
Simple Regression: (BEA, BLS, Urban Data Catalog)
Predictor
Coefficient
p-value
R-Squared
Prop of Cost Burdened
0.0023198
0.2313
0.0004576
Prop of Severe Cost Burdened
0.0139008
8.806E-05
0.004901
Prop of Non-White Homeowners
0.0166569
<2E-16
0.1169
Median Owner Cost
-5.660E-08
0.9
5.063E-06
RGDP
2.992E-11
1.129E-07
0.00894
Unemployment Rate
0.0629692
1.113E-09
0.01177
Marital Rates
0.0207124
0.01732
0.001806


Figure 4
Multiple Regression: (American Community Survey)



	In Table 6, there are four elements that have a p-value that is lower than 0.05: RGDP, race, martial rate, and education level which means they have statistical significance on the predicted foreclosure rate. Figure 7 unexpectedly that unemployment rates and cost-to-income ratio are not statistically significant. Both those variables would be directly correlated with how much money a person would be able to pay for mortgage payments. Although they are not statistically significant, does not mean those variables are not correlated with foreclosure rates. Counties with higher proportions of residents that are married with present spouses decrease the probability of being foreclosed on. It seems at any education level, there is always an increased risk of being foreclosed on, which is not expected, since higher educational attainment usually leads to higher incomes. However, it is important to note that between both Table 6 and Figure 4 all have relatively low R-Squared values, which means they all do not explain large proportions of variance in the predicted foreclosure rates.

Discussion
	Based on our results and not accounting for low R-Squared values, 
	
Our team faced many challenges in this analytics project. From issues with data sourcing to trouble with modeling success, we overcame many obstacles. 

Though the American Rescue Plan Act claimed Indigenous tribes would receive HAF funding, our source from the U.S. Department of the Treasury does not specify how much money tribes received. Additionally, the Census API data which we joined with our dataset had different values for “median homeowner cost” than our original Urban Catalog data, despite the two datasets claiming to have the same source. We believe that the difference could be due to inflation since one source was published in 2019 and another was published later but was representative of 2019. We used the dataset from Urban Catalog as our foundation for this project, but we are unsure about how its data was collected. There is no clear connection to IPUMS, Census.gov, or anything noting Urban Catalog did the data collection themselves. Though Urban Catalog claims to source from the American Community Survey data, we believe that this is only one of multiple sources of the dataset since there are discrepancies between the Urban Catalog dataset and the American Community Survey data. Also, there was no clear method on how predicted foreclosure rates were constructed. 

We also dealt with missing data. Our original dataset had counties that were missing data for many variables. Despite building many models, our final r-squared value was only 11 percent. This means our model could predict the outcome correctly 11 percent of the time. We used linear modeling, however, most data is not fit for a linear model, especially social-economic data due to the interrelationships between many variables. For example, there are systematic connections between race and money that do not translate well to a linear model. Finally, the fatal flaw of our data is that it attempted to predict the impact of COVID-19 on the American people but used pre-pandemic data. Obviously, people who were at-risk in 2019 likely faced financial hardships in 2020 and 2021. However, the pandemic impacted Americans in unexpected and unprecedented ways. The Homeowner Assistance Fund was created to support homeowners facing financial hardship associated with COVID-19 and the 2019 data does not give the full picture of how homeowners were truly impacted.



Works Cited (Victoria will edit for voice and double check citations, formal citations, no designated format)
US Bureau of Labor Statistics. “American Community Survey (ACS) Questions and Answers.” U.S. Bureau of Labor Statistics, 6 Dec. 2019, www.bls.gov/lau/acsqa.htm#:~:text=The%20ACS%20is%20a%20large,3.5%20million%20household%20addresses%20annually. 
Federal Communications Commission. “Federal Information Processing System (FIPS) Codes for States and Counties.” Federal Communications Commission, transition.fcc.gov/oet/info/maps/census/fips/fips.txt. Accessed 7 June 2023. 
Ratcliffe, Janneke, et al. “Homeowner Assistance Fund County-Level Targeting Data.” Urban Data Catalog, 5 Oct. 2021, datacatalog.urban.org/dataset/homeowner-assistance-fund-county-level-targeting-data. 
Bureau of Economic Analysis. “Gross Domestic Product by County, 2019.” Gross Domestic Product by County, 2019 | U.S. Bureau of Economic Analysis (BEA), 9 Dec. 2020, www.bea.gov/news/2020/gross-domestic-product-county-2019. 
US Census Bureau. “American Community Survey (ACS).” Census.Gov, 15 May 2023, www.census.gov/programs-surveys/acs. 
“Homeowner Assistance Fund | U.S. Department of the Treasury.” Home.treasury.gov, home.treasury.gov/policy-issues/coronavirus/assistance-for-state-local-and-tribal-governments/homeowner-assistance-fund.
“Text - H.R.1319 - 117th Congress (2021-2022): American Rescue Plan Act of 2021.” www.congress.gov, 10 Mar. 2021, www.congress.gov/bill/117th-congress/house-bill/1319/text.
https://www.congress.gov/117/bills/hr1319/BILLS-117hr1319enr.pdf 63/242
https://www.congress.gov/116/plaws/publ260/PLAW-116publ260.pdf 891/2126
https://www.congress.gov/116/plaws/publ94/PLAW-116publ94.pdf 444/716
“Collections & Data Sources : Handbook of Methods: U.S. Bureau of Labor Statistics.” www.bls.gov, www.bls.gov/opub/hom/cex/data.htm#:~:text=The%20Bureau%20of%20Labor%20Statistics.
“Information Quality Guidelines | U.S. Bureau of Economic Analysis (BEA).” Www.bea.gov, www.bea.gov/about/policies-and-information/information-quality#:~:text=BEA%20receives%20data%20from%20a.


Last, First. “Title of Article.” Organization it is With, 7 Apr 2019, https://www.congress.gov/116/plaws/publ94/PLA. Accessed 8 June 2023. 






Our data is from the Homeowner Assistance Fund. It targets the county level. Here is the link to the original dataset: https://datacatalog.urban.org/dataset/homeowner-assistance-fund-county-level-targeting-data 


Our dataset contains data on:
Homeowners’ demographic
Income characteristics
Foreclosure rates

Dimensions:
Each observation represents a county or other census area in the U.S.
3141 observations
23 variables
98 observations have missing data


Intro to Our Dataset - Definitions
PUMA Estimate: Population estimate because the county had <100,000 people.

Homeowner: Someone who owns their home and does not pay a mortgage.

Mortgages: Homeowners with outstanding mortgages. (This dataset counts people with mortgages as homeowners even though they do not own their home.)

Less % AMI: Number of homeowners earning less than % of area-median-income.

100-150 AMI: Middle to upper income.

Mortgage Share: Total mortgages / Total homeowners

Cost Burdened: Spending 30% or more of annual income on housing costs.

Severely Cost Burdened: Spending 50% or more of annual income on housing costs.
