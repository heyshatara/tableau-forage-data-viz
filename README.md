# Using Tableau Data Visualizations to Make Informed Business Decisions

<img src="https://imgur.com/HbBdjXK.png" height="50%" alt="Data Analysis Image by Nikin from Pixabay"/>

<h2>🗺️Project Description</h2>
This data visualization portfolio project is part of the Forage Internship Job Simulation in partnership with Tata Insights.
An online retail store has hired me as a consultant to review their business performance provide marketing & operations insights that would be valuable to the CEO and CMO of the business. The business has been performing well and the management wants to analyse what the major contributing factors are to the revenue so they can strategically plan for next year.

<h2>💻Languages/Libraries and Utilities Used</h2>

- <b>Tableau</b> 
- <b>Excel</b>

<h2>📝Dataset Description:</h2>
Online Retail Dataset Provided by Tata, made available from UC Irvine Machine Learning Database https://archive.ics.uci.edu/datasets.

<h2>🧹Internship Tasks</h2>

#Task 1: Framing the Business Scenario
- Draft quantitative and qualitative questions you think would be important and relevant to the CEO & CMO based on the Online Retail Dataset shared with you
- Skills used: `data visualization` `data analysis` `data interpretation`

#Task 2: Choosing the Right Visuals 
- Showcase understanding of business requirements for various provided scenarios, and recommend the appropriate visuals/graphics
- Skills used: `data visualization` `charts & graphs` `visual basics`

#Task 3: Creating Effective Visuals
- a. Clean data
- b. Using your BI tool of choice, create visuals around four questions requested by the CEO & CMO.
- Skills used: `data visualization` `tableau` `dashboard` `data cleanup` `excel`

#Task 4: Communicating Insights and Analysis 
- Effectively communicate your findings and explain how it relates to the concerns of the CEO & CEO
- Skills used: `analysis & presentation` `effective communication` `analytics & insights`


<h2>📈Tableau Visualization Breakdown</h2>
Break down average value per Free Trial by Region and analyze differences in values.

- Introduce and group by the additional dimension: `region`. Call the resultant table `cohort_value_by_month_and_region.

```bash
with free_trials_and_purchases as (
	select
            trials.trial_id
        ,	trials.free_trial_start_date
        ,	trials.region
        ,	purchases.purchase_date
        ,	purchases.purchase_value
    from trials
        left join purchases
            on purchases.trial_id = trials.trial_id
)

,	summary_by_month as (
    select
            date_trunc('month', free_trial_start_date) as month
    	,	region
        ,	count(*) as num_free_trials
        ,	count(purchase_date) as num_purchases
        ,	sum(purchase_value) as usd_value
    from free_trials_and_purchases
            group by 1, 2
)

select
		month
    ,	region
	,	num_free_trials
    ,	num_purchases
    ,	usd_value
    ,	(usd_value::float) / (nullif(num_free_trials, 0)::float) as cohort_value_per_free_trial
from summary_by_month
	order by 1, 2
```
<img src="https://i.imgur.com/Cj9vnak.png" height="40%" alt="Table - Cohort Value Per Free Trial"/> 

- Create a graph of `cohort_value_per_free_trial`.
<img src="https://i.imgur.com/NEwVyDv.png" height="80%" alt="Line Graph Cohort Value Per Free Trial by Month and Region"/>


 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
