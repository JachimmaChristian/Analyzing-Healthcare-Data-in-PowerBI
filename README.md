# Analyzing-Healthcare-Data-in-PowerBI
In healthcare, improving efficiency while maintaining high-quality patient care is a top priority. In this PowerBI Case study, I explored a real-world dataset to uncover hospital efficiency insights, I analyzed attributes impacting the patient's length of stay (LOS) and cost and worked to identify factors contributing to hospital differences. 

I leveraged my DAX skills to create measures and generate insightful visualizations. To finish off, I brought it all together in a sophisticated business dashboard to communicate insights to the team. 

This case study gave me a chance to practice a range of Power BI skills, working with real-world data.  

**Skills Demonstrated** 
1. Data modeling
2. Exploratory data analysis
3. Root cause analysis
4. DAX calculations and
5. Report design.

Enough with the chitchat let's dive in!



# The Problem
In this case study, a fictitious consulting company called HealthStat has hired me to uncover insights on potential hospital efficiency opportunities, and they would like me to analyze a state-wide hospital dataset and leverage my Power BI skills to create an engaging dashboard of insights.


# Dataset & Data Model
The dataset was provided by Healthstat. They've captured patient-level data on all hospital stays in a single year for elective hip replacement surgeries across the state of New York.

The dataset is one single table with 30 columns. Each row in the dataset represents a single inpatient stay, from their admission to discharge date. The health information in this dataset is not individually identifiable (This means the file does not contain any personal health information).

The dataset has some key attributes to analyze efficiency: Length of stay measured in total days and Total costs attributed to each hospital stay.

![](healthcare1.png)

Here's a list of some of the key columns of interest for the case study:

facility_id, 

age_group, 

patient disposition, 

diagnosis description, 

severity of illness, and risk of mortality. 

We will closely evaluate these (and others) in the case study as we work to understand what factors impact the length of stay and related costs.


# Case Study Details
In healthcare analytics, there are several quality metrics to be considered but for this case study, our focus is on efficiency, which is all about avoiding waste. This includes minimizing waste of equipment, supplies, ideas and energy.

Length of stay (or LOS) is considered an important indicator of the efficiency of hospital management. It's calculated as the total duration in days of a patient's stay in a hospital. A shorter LOS is often desirable in hospital operations. Although, many factors can impact LOS. Patient age, health status, the type of procedure (or surgery), whether or not there were any complications, and the size of the hospital are some common factors.

Here are some terms you will encounter throughout this case study: 

An inpatient: is a person who has been admitted to a hospital bed. 

A discharge: is defined as the release of a patient from hospital care by a medical worker. 

Disposition: This is the patient destination or status upon discharge, for instance to another facility or home. 

An elective surgery: is a procedure that was planned, in other words, it was not due to an emergency.

In this case study, the focus is on patients who received hip replacement surgery. Here's a bit of a background on what this procedure is all about. Patients with hip pain, typically arthritis, may require elective hip replacement surgery. In this procedure, damaged bone and cartilage are surgically removed and replaced with prosthetic components. 

Hospital stays can range from 0 to 2 or more days.


#  Exploratory Analysis Of The Dataset

I loaded the data into the PowerQuery editor to investigate it for errors and performed some exploratory analysis. I removed all the rows of data where the description was not "HIP REPLACEMENT, TOT/PRT" and I created a _Measures table to host my measures. I then created a measure called "Total Hospitals" to show the Distinct count of hospitals.

![](healthcare2.png)

After creating measures to analyze hospital totals, I visualized these measures to get a sense of how many hospitals in the state do our procedure of interest.

![](healthcare3.png)

To build an understanding of patient profiles in the dataset I explored the preliminary demographics such as gender and age and created a measure "Total Discharges" to count total discharges in the dataset and stored it in the _Measures table. 

HealthStat assigned a clinical advisor to direct me in some of my tasks, to help guide my analysis from a clinical perspective, the clinical advisor requested to see a breakdown for patients aged 50 and older. I modified my visualization of gender distribution by age group to account for this change.

![](healthcare4.png)

After establishing some key information about total hospitals and discharges in the dataset along with some interesting demographics on the patient profile. It was time to explore how length of stay (LOS) days varied across the demographic fields. I created a measure (Average LOS Days) to calculate the average length of stay days and stored the measure in the _Measures table.

I created two visualizations to show the average LOS days by age group and gender, again I filtered to assess patients aged 50 or older. To do this I created a new column called "Age Band" and assigned a value of "Age 50+" if age 50+ and "Age <50" if not. I replaced the age_group with this new field.

![](healthcare5.png)

The leadership team at HealthStat want to see how average LOS days and total discharges compare between hospitals. The clinical advisor also added for me to factor in the total number of practising surgeons by the hospital.

I created a line and stacked column chart to visualize both the total discharges by hospital and the average LOS days and set the visualization to show only the top 15 hospitals by total discharges.

Next, I created a new measure that calculates the count of surgeons and included that measure in my chart of LOS and discharges by hospital as a tooltip. 

![](healthcare6.png)

# Findings from our exploration 

1. 151 hospitals in New York State perform elective hip replacement surgeries.
2. With over 26thousand (26,286) total discharges
3. The average LOS was 2.65 days for the procedure although there was significant variability between hospitals.
4. Although we have explored LOS against some demographics such as age and gender, we are yet to understand the reason behind the variability in LOS between the hospitals.

Going forward, let's look at the Average cost per discharge, I calculated this by dividing the sum of total costs by the sum of total discharges. This metric will serve as a benchmark to compare cost efficiency between hospitals and highlight areas for efficiency improvement.

Factors that can impact the cost of patient stay include:

1. Patient severity of condition
2. Age
3. Size of hospital
4. Procedure and type of equipment used.

We'll be exploring which hospitals stand out with the highest cost and LOS relative to the state average and which hospitals stand out as the biggest outliers overall. We'll also explore to see if a larger surgical program size impacts LOS and Cost and we'll perform a root cause analysis to find out what factors influence LOS and Cost the most.

The average cost per discharge and the average LOS vary per hospital facility. So I created two metrics to quantify the relative difference between each hospital vs the overall state average.  

I created two measures to compute overall state averages, one for Average cost per discharge and another for average LOS days and labelled the measures with ALL at the end of the name.

Average Cost Per Discharge All| Average LOS Days All
:-----------------------:|:---------------------------:
![](healthcare8.png)                    |![](healthcare9.png)    

I built another two measures to calculate the percentage difference in Average Cost per Discharge and the percentage difference in LOS days called "% Var Average Cost per Discharge" and "% Var Average LOS Days" respectively. 

% Var Average Cost per Discharge|% Var Average LOS Days
:-----------------------:|:---------------------------:
![](healthcare10.png)                    |![](healthcare11.png)    

I placed these measures in a table visual and used conditional formatting to indicate where values of average cost and LOS days are higher or equal to the overall values. 

Let's investigate further to see which hospitals stand out as outliers. We'll be using a dynamic quadrant chart to achieve this. 

![](healthcare7.png)

To highlight the outliers I created a Scatter chart that displays Average LOS Days vs Average Cost per Discharge with each hospital as a distinct dot and added two average lines to the chart. To enhance the chart further I added Total Discharges as bubble size and coloured the bubbles by health service area. Lastly, I added one more reference line for the 90th percentile so that values that fall outside this line are our outliers. 

![](healthcare12.png)

Before diving into the root cause analysis, my boss asked me to account for surgical program size. Our source data doesn't explicitly state the surgical program size, so I created a new table using DAX functions that summarize total discharges and surgeons by hospital next I updated my data model to join the hospital_discharges table with the surgical_program_volume_summary table, I grouped the Total discharges in 200s then labelled them into a more defining group that became our column for Surgical Program Size.

 surgical_program_volume_summary table created using Dax |    Data Modelling    | Surgical Program Size column created using Dax
:---------------------------:|:---------------------:|:---------------------:
![](healthcare13.png)          |![](healthcare15.png)  |![](healthcare14.png)

Now let's proceed to investigate the root cause impacting cost and LOS, the clinical advisor has provided a list of factors that they want to assess:

Risk of mortality
Severity of illness description
Diagnosis description
Patient disposition
Gender
Age Bins
Surgical program size
Health service area

I created a column chart for each of the above factors to summarize the Average LOS Days, looking at the charts we see that some factors stand out above others but it's still not easy to tell which factor most influences average LOS days. 

![](healthcare16.png)

I introduced the Key influencer visual bringing in the eight variables assessed above, I used the key influencer visual to assess both the Average LOS Days and the Average Cost Per Discharge. 

![](healthcare17.png)

Key Insights uncovered: 

1. Average cost per discharge was $20,910 and there was significant variability between hospital facilities
2. The root cause analysis uncovered that some attributes stood out over others to influence both cost and average LOS. Top influencers increasing average LOS and cost:

Extreme illness severity
Extreme/ Major mortality risk 

These two stood out as having the most significant impact on reduced efficiency.

3. Hospitals in New York City had the highest LOS and cost overall
4. LOS was influenced by patient disposition to a skilled nursing home

Final Dashboard: Conclusively, I put all the visual subsets of insights into a report template and loaded the Healthstat branding into it. I created a “Home” page and provided users with quick access to navigate between pages in the report.

The HealthStat team now has a cohesive report that will enable their understanding of the key impacts on average LOS and cost for hospitals across New York. This will inform them of where targeted quality improvements can be made to improve both the hospital's operational efficiency and patient experience.

Click [Here](https://www.novypro.com/project/case-study-analyzing-healthcare-data) to interact with the dashboard. You can also view the pdf of the final report [Here](https://github.com/JachimmaChristian/Analyzing-Healthcare-Data-in-PowerBI/blob/main/Analyzing%20Healthcare%20Data.pdf) 



