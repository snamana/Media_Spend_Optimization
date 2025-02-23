# Media Spend Cost Optimization


### Team Members
- **Aditya Sanjay Pawar**: [GitHub](https://github.com/aspawarsyredu)
- **Himanshu Hegde**: [GitHub](https://github.com/himanshu-hegde-syr) (Point of Contact)
- **Keerthi Krishna Aiyappan**: [GitHub](https://github.com/KeerthiKrishna-Aiyappan)
- **Sri Venkata Subhramanya Abhishek Namana**: [GitHub](https://github.com/snamana)

### Introduction

#### Marketing Mix Model (MMM)
The Marketing Mix Model (MMM), also known as the Media Mix Model, is utilized by companies to measure the impact of their media spending (including TV, social media, email, newspapers, etc.) on sales. This analysis helps in optimizing future budget allocations. As companies invest millions into various marketing channels, both offline and online, to drive customer acquisition and sales, the complexity of tracking, analyzing, and quantifying the effectiveness of these investments increases.

Factors influencing the sale of a product include:
- **Brand image**
- **Product distribution**
- **Product pricing**
- **Offline and online media spend**
- **Competitor pricing and media spend**
- **Discounts and promotions**
- **Seasonality**
- **External economic factors**

When you have multiple factors affecting the demand for your product, it is crucial to understand and be able to quantify how each media channel you spend on (TV, social media, email, newspapers etc.) impacts your demand. This understanding is all the more essential while optimizing the budget for company media spend, by allocating spend across different media channels efficiently.

#### What we are doing to solve this
The solution we are proposing involves using Bayesian and Shapley based approaches to understand the marginal(individual) contribution of each media channel to sales, the diminishing effect media spend has, ad-stock lag effect of each media channel and the cost saved by optimizing media spend.

Our goal is to:
1)	Understand the effectiveness of different media channels in driving product sales.
2)	Quantify Ad-Stock effect of various media channels. Ad-stock is the lagged effect between advertisement launch and consumer purchase.
3)	Assess the Diminishing Returns of each media channel. After a certain saturation point, increasing media spend will not result in increased product sales (i.e. it will result in diminishing sales returns).
4)	Optimize future marketing decisions and quantify its impact. Once we have a clear understanding on the marginal impacts of each of the media channels, we can optimize our media spends given a certain budget. 


#### What is new in our approach?
Traditional MMM models over the years have been built using Generalized Linear models and Bayesian Statistics. Over the past few years, Shapley(Shapley Additive exPlanations) based approaches have been highly used across different domains for calculating marginal contributions of different features of a non-linear model to the target variable. However, they have not been implemented across many MMM models. We intend to explore using Shapley to understand the relationship and impact of each of the media channels towards product demand  and compare these insights to ones obtained by traditional methods.

#### If you are successful, what difference will it make?
A successful model will result in an optimized media allocation budget and strategy, which in turn will increase demand for products, yield more revenue and help reduce unnecessary spending.
Some examples of the insights are:
#### Marketing Insights Examples
- TV ads contribute to **20% of sales revenue**, while social media accounts for **10% of the sales revenue**.
- Consumers typically start purchasing a product **2 weeks after seeing TV ads**, and **1 week after seeing newspaper ads**.
- Increasing the social media spending for product A above **10000** dollars yields no increase in sales returns.
- Reducing the total media spend budget to **30,000** dollars and allocating **6,000** dollars of it to newspaper ads can lead to a **4% rise in product sales**.


### Literature Review on Marketing Mix Modeling

In today’s world, marketing mix modeling is predominantly conducted using additive techniques or multiple linear regression algorithms. The Adstock effect is employed to capture the prolonged and cumulative impact of advertising, enabling marketers to fine-tune the timing and effectiveness of campaigns. Saturation Effects help identify the point of diminishing returns on marketing investments, which is crucial for efficient budget allocation. Not all companies consider the adstock effect or saturation effect in their model building, and this is an aspect we aim to incorporate. We will also consider seasonal and cyclical trends that might affect the sales of our product.

**Edwin Ng, Zhishi Wang and Athena Dei [2021]**: Utilized Bayesian and varying coefficient models to enhance Marketing Mix Modeling at Uber. Bayesian models were preferred due to their efficiency in training on small datasets, which is common in marketing data, often available only at the geographic/national level.

**Jessika Karlsson [2022]**: Developed marketing mix solutions using Bayesian Structural Time Series (BSTS), incorporating prior beliefs into the distributions of the model parameters. The use of priors in Bayesian modeling allowed for the incorporation of prior domain knowledge about competitor product pricing, thereby enhancing model accuracy.

**Slava Kisilevich [2022]**: Employed tree-based ensembles and utilized SHAP (Shapley Additive Explanations) to explain media channel performance. SHAP, a game-theoretic approach, helps explain the output of machine learning models, revealing how much each feature contributes to individual predictions. His methods demonstrated high consistency with previously implemented Bayesian marketing mix models.

There are several open-source libraries like **mamimo**, **Py-McMarketing**, and **LightweightMMM** that could be useful in our approach to modeling.


### SHAP (SHapley Additive exPlanations)

SHAP is a technique for interpreting machine learning models by providing explanations for the predictions they make. It leverages the concept of Shapley values from game theory to fairly allocate the influence of each feature on the model's prediction.

#### Key Concepts:
- **Shapley Values**: Originally developed in game theory to distribute gains among players based on their contribution, these values are applied in machine learning to quantify the contribution of each predictor variable (or feature) to the prediction.
- **Model Output Explanation**: SHAP assigns an importance value to each feature for a particular prediction, calculated by assessing the impact of each feature when added to a model that predicts the expected output.
- **Combinatorial Approach**: SHAP considers all possible combinations of features, determining how the presence or absence of a feature impacts the prediction, ensuring fairness and consistency in the contributions measured.

#### Interpretations and Tools:
- **Individual and Global Interpretations**: SHAP values can explain individual predictions, offering insights into specific decisions made by the model. Aggregating SHAP values provides a view of the overall importance and effect of features across the dataset.
- **Tool Integration**: SHAP is compatible with major machine learning frameworks like scikit-learn, XGBoost, TensorFlow, and more, implemented in Python.
- **Visualizations**: SHAP offers visual tools for interpretation, including:
  1. **Force Plots**: Show how each feature contributes to individual predictions.
  2. **Summary Plots**: Offer a global view of feature importance and effects.
  3. **Dependence Plots**: Explore interaction effects between features.

#### Properties of SHAP Values:
- **Additivity**: The contributions of individual features to the prediction can be independently calculated and summed, allowing for efficient computation.
- **Accuracy**: SHAP values sum to the difference between the expected model output and the actual output for a given input, providing precise local interpretations.
- **Robustness**: SHAP values are zero for irrelevant or missing features, ensuring that interpretations are not distorted by such data.
- **Consistency**: SHAP values remain stable across model changes unless the contribution of features changes, offering a reliable interpretation of model behavior.


#### Stakeholders in Marketing Mix Modeling

1. **Chief Marketing Officers (CMOs) and Marketing Teams**:
   - CMOs face increasing pressure to demonstrate the tangible value of marketing efforts, especially under challenging economic conditions. They rely on MMM to justify marketing expenditures by linking them to sales impacts and to make informed decisions on budget allocation across various channels to optimize media performance.

2. **Finance Departments**:
   - Finance teams are keen on understanding the return on investment (ROI) from marketing activities to ensure efficient use of budgets. They need clear and reliable metrics that correlate marketing spend with sales outcomes, aiding in financial planning and forecasting.

3. **Brand Managers**:
   - Responsible for specific products or brands within a company, brand managers need to gauge how their marketing strategies contribute to brand awareness, customer acquisition, and sales. They require detailed insights into the effectiveness of various marketing tactics within their specific brand context.

4. **Sales Teams**:
   - Sales departments benefit from insights on how marketing activities influence customer behavior and sales cycles. They require data that assists in aligning sales strategies with marketing initiatives to maximize overall business performance.

5. **Data Analysts and Data Engineers**:
   - These technical stakeholders are involved in aspects of MMM such as data collection, model building, and analysis. They manage the data, provide necessary business context, validate insights, and offer feedback on the findings.

6. **Product Development Teams**:
   - Product development can be informed by insights from MMM, highlighting customer preferences for certain features or benefits. These teams need information on how marketing for existing products affects customer perceptions, which can guide the development of new products or improvements to existing ones.


### Data and Methods

#### Data
The marketing spend data for a shampoo advertiser is provided by Neustar MarketShare and consolidated from sources such as Kantar Media, IRI, ITG, JD Power, and Rentrak. This dataset includes 4 years of weekly data covering weekly volume sales in ounces and media spend across major channels like TV, magazines, display, YouTube, and search. Additional variables include the average price per ounce, ACV weighted product distribution, discounts, and promotions. This dataset was previously used by Yuxue Jin and Yueqing Wang in their 2017 marketing solution for Google.

**Categories of Data Columns:**
1. **Media Variables**
   - Media Impression (`mdip_`): impressions across 13 media channels.
   - Media Spending (`mdsp_`): spending across these media channels.
2. **Control Variables**
   - Macro Economy (`me_`): CPI, gas prices.
   - Markdown (`mrkdn_`): discounts.
   - Store Count (`st_ct`).
   - Retail Holidays (`hldy_`): one-hot encoded.
   - Seasonality (`seas_`): months, with Nov and Dec broken down further into weeks.
3. **Target Variable**
   - Sales (`sales`): Weekly sales in dollars.

#### Methods
The methodology will follow these steps:
1. **Data Pre-processing**
   - Handling null/missing values.
   - Correct data typing.
   - Ensuring data integrity.
2. **Exploratory Data Analysis (EDA)**
   - Visual representations to explore data distributions and patterns.
   - Outlier and correlation analysis.
   - Data summary across various hierarchies.
3. **Feature Engineering**
   - Selection and creation of relevant features.
   - Encoding categorical and standardizing continuous features.
   - Handling missing data.
4. **Modelling**
   - Use of Bayesian models and tree-based boosting methods.
   - Shapley analysis for understanding individual media contributions.
   - Model accuracy tracking with RMSE and MAPE.
5. **Insight Validation and Feedback**
   - Model performance reviews and iterative feature and parameter adjustments.
   - Exploration of alternative modelling approaches.
6. **Cost Optimization Simulations**
   - Running simulations for various budgeting decisions.
   - Calculating ROAS (Return on Ad Spend) for different scenarios.


### Marketing Mix Modeling Workflow - 1

1. **Standard Pre-processing Techniques**
   - Handle null values, apply one-hot encoding, and perform scaling on the data.

2. **Transform Non-linear Columns**
   - Address Ad stock/Carryover, and apply Hill saturation transformations to relevant columns.

3. **Define Prior Distribution**
   - Set prior distributions for media spend, seasonal effects, and control features.

4. **Run Bayesian MMM Model**
   - Implement the Bayesian MMM model using Lightweight MMM and plot the posterior distributions.

5. **Analyze Baseline Spend**
   - Evaluate the impact of each advertising channel over several weeks.

6. **Analyze Response Curves**
   - Study the diminishing returns of different advertising channels.

7. **Optimize Budget and Maximize ROI**
   - Conduct budget optimization exercises to maximize return on investment.


### Marketing Mix Modeling Workflow - 2

1. **Standard Pre-processing Techniques**
   - Apply null value treatment, one-hot encoding, and scaling to prepare the data for modeling.

2. **Define Ad-stock Decay**
   - Establish the decay parameters for Ad-stock to model the carry-over effects of advertising spend.

3. **Define Optuna Hyperparameters**
   - Set up hyperparameters for the model and Ad-stock decay using Optuna to minimize error and the root sum square deviation (RSSD) between spend share and effect share.

4. **Run Model and Select the Most Accurate**
   - Execute the model and choose the most accurate one based on performance metrics.

5. **Interpret and Analyze Response Curves**
   - Study the diminishing returns and the relationship between spend-share and effect-share through response curve analysis.

6. **Optimize Budget and Maximize ROI**
   - Use SciPy Optimize to adjust the marketing budget, adding constraints and boundaries to maximize return on investment.


### Results 




#### Lightweight MMM Model - 1

INSERT - FROM GOOGLE DOC
The graph above compares actual and predicted key performance indicators (KPIs) in relation to their contribution to sales. The predicted values generally follow the trend of the actual data, demonstrating that the model reasonably captures the overall pattern. However, the model struggles with peaks, tending to underestimate the true sales values. The R-squared value of 0.672 suggests that the model explains a significant portion of the variations, indicating a good fit, yet highlighting that there is still room for improvement.


INSERT HERE TOO
This chart shows the contribution of different media channels to sales, with the bars representing the average estimated impact of each media type. The lengths of the bars show the relative importance of each channel—taller bars mean a higher contribution. The error bars on each bar represent the 95% high density interval, indicating where the true value is likely to fall most of the time, which helps us understand the certainty of the estimates.

Direct mail, TV, and online display media have taller bars, suggesting they are more influential in driving sales compared to other channels like newspaper and radio. On the other hand, social media and search engine marketing (SEM) show moderate contributions. The large error bars on some media like TV and direct mail indicate more variability in their effectiveness estimates, suggesting that their impact might not be consistent across different scenarios or campaigns. 

INSERT HERE TOOThis chart provides an overview of the return on investment (ROI) for different media channels, which tells us how effective each media type is in generating returns compared to the amount invested. The heights of the bars indicate the average ROI for each channel, with taller bars signifying higher returns. TV and digital video have some of the highest returns, suggesting they are highly effective compared to other channels. On the other hand, direct mail and search engine marketing (SEM) show relatively lower returns. The error bars extending from each bar show the range of possible ROI values, reflecting uncertainty in the estimates. Large error bars, as seen in channels like TV and newspaper, indicate that the ROI for these channels can vary widely. 

INSERT HERE TOO
The first chart compares budget allocations before and after optimization for ten different channels, including direct mail, inserts, newspapers, digital audio, and more. Notably, before optimization, the budget was somewhat evenly spread across the channels, with the highest allocation to channel 0 (direct mail) and channel 9 (search engine marketing). After optimization, the allocation changes dramatically: the budget for channel 9 (search engine marketing) is significantly increased to 36%, and the budget for channel 1 (insert) is also raised to 27%. This suggests that these channels were identified as having higher returns on investment or effectiveness in achieving sales targets.

The second chart shows the predicted sales targets before and after budget optimization using lightweightMMM’s own optimizer. There is a noticeable increase in the predicted sales target from approximately $713.9 million to $728.2 million. This demonstrates that the optimized budget allocation is expected to enhance sales outcomes by leveraging channels that potentially deliver better performance.

The following is what each channel represents from the first image: 

channel_0: direct mail,          	channel_1: insert,
 channel_2: newspaper,          	channel_3: digital audio,
 channel_4: radio,                    	channel_5: tv,
 channel_6: digital video,       	channel_7: social media,
 channel_8: online display,     	channel_9: sem


#### Shap Based Model - 2

INSERT HERE
This graphic above illustrates how our xGBoost model tried to predict each of our test values. As we can see from above, we have a general adjusted R squared of 53.5, and we can clearly see from above that the model is able to capture the middle ground correctly, it can do better while dealing with the highest peak and lowest troughs. 

INSERT HERE
The above graph tells us about how important a feature is in the model - about diminishing returns. The ones in green impact sales positively, while the ones in red impact it negatively. We can see that media spend on sem, media impressions on sem and media spend on inserts contribute the most positively, while media impressions in digital audio, newspaper and radio have the most negative contribution to sales but they are still very important features from a model perspective. 

INSERT HERE

The three graphs depict how long it takes for returns to diminish on a media channel. Direct Mail Media Spend accounts for 32% of the total budget but has minimal impact on sales. SEM media spend accounts for 28% of the total budget, and has a very high (>$2.5 million above the average) marginal impact on sales. Newspaper media spend has a neutral marginal impact on sales.

INSERT HERE
Upon adding constraints that the optimized budget should not differ from the original budget by 20%, the above is our optimized budget solution. The bars in blue are the original spend while the ones in orange are the optimized spend. 


### Risks in Marketing Mix Modeling

Some of the factors that affect the quality of an MMM model include:

1. **Access to Competitor Data**:
   - Competitor product pricing and media spending are often not available. These variables must be accounted for in the model as unexplained variance in the target variable.

2. **Mismatch in Data Hierarchy**:
   - Media spend and product level sales are often recorded at different levels — media spend at a geographic or national level, and product sales at a product level. This mismatch leads to smaller datasets and limits the accuracy of granular level insights, particularly for individual campaigns.

3. **Granularity of Insights**:
   - Marketing Mix Modeling does not always generate granular level insights and is usually paired with other processes like Multi-Touch Attribution as part of a larger pipeline of analytics solutions to optimize media spend.

4. **Complete Visibility into Offline Media Channels**:
   - Companies often lack complete visibility into the extent of reach their offline media channels achieve. For example, a company might invest $1 million in newspaper ads but not have detailed access to data about the readership demographics and regional distribution.

5. **Evolving Advertising Landscape**:
   - The dynamic nature of the advertising world means that strategies that were effective yesterday might not work tomorrow. It is crucial for our project to regularly update our methods and information to keep pace with these changes.

### References

1. Edwin Ng, Zhishi Wang, Athena Dai [2019]:
   - "Bayesian Time Varying Coefficient Model with Applications to Marketing Mix Modeling."
   
2. Jessika Karlsson [2022]:
   - "Bayesian Structural Time Series in Marketing Mix Modelling."


PENDING WORK: 
1) Discussion
2) Future Work
3) Add Shap image in Literature Review
4) Add adstock and saturation effect image in Literature Review 
5) MODIFY RSULTS


```python

```
