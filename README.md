# Analyzing-Healthcare-Data-in-PowerBI
In healthcare, improving efficiency while maintaining high-quality patient care is a top priority. In this PowerBI Case study, I explored a real-world dataset to uncover hospital efficiency insights, I analyzed attributes impacting the patient's length of stay (LOS) and cost and worked to identify factors contributing to hospital differences. 

I leveraged my DAX skills to create measures and generate insightful visualizations. To finish off, I brought it all together in a sophisticated business dashboard to communicate insights to the team. 

This case study gave me a chance to practice a range of Power BI skills, working with real-world data.  

Enough with the chitchat let's dive in!


# The Problem
In this case study, a fictitious consulting company called HealthStat has hired me to uncover insights on potential hospital efficiency opportunities, and they would like me to analyze a state-wide hospital dataset and leverage my Power BI skills to create an engaging dashboard of insights.


# Dataset & Data Model
The dataset was provided by Healthstat. They've captured patient-level data on all hospital stays in a single year for elective hip replacement surgeries across the state of New York.

The dataset is one single table with 30 columns Each row in the dataset represents a single inpatient stay, from their admission to discharge date. The health information in this dataset is not individually identifiable. This means the file does not contain personal health information.

The dataset has some key attributes to analyze efficiency. Length of stay measured in total days and Total costs attributed to each hospital stay.

![](healthcare1.png)

Listed here are some of the key attributes of interest for the case study, these include 
facility_id, 
age_group, 
patient disposition, 
diagnosis description, 
severity of illness, and risk of mortality. 

We will closely evaluate these (and others) in the case study as we work to understand what factors impact the length of stay and related costs.


# Case Study Details
In healthcare analytics, there are several quality metrics to be considered but for this case study, I'll focus on efficiency, which is all about avoiding waste. This includes minimizing waste of equipment, supplies, ideas and energy.

Length of stay (or LOS) is considered an important indicator of the efficiency of hospital management. It's calculated as the total duration in days for a patient stay in a hospital. A shorter LOS is often desirable in hospital operations. Although, many factors can impact LOS. Patient age, health status, the type of procedure (or surgery), whether or not there were any complications, and the size of the hospital are some common factors.

Here are some terms you will encounter throughout this case study: 

An inpatient: is a person who has been admitted to a hospital bed. 

A discharge: is defined as the release of a patient from hospital care by a medical worker. 

Disposition: This is the patient destination or status upon discharge, for instance to another facility or to home. 

An elective surgery: is a procedure that was planned in advance, in other words, it was not due to an emergency.

In this case study, the focus is on patients who received hip replacement surgery. Here's a bit of a background on what this procedure is all about. Patients with hip pain, typically arthritis, may require elective hip replacement surgery. In this procedure, damaged bone and cartilage is surgically removed and replaced with prosthetic components. 

Hospital stay can range from 0 to 2 or more days.


#  Exploratory Analysis Of The Dataset
