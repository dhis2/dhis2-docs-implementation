# Meatdata Assessment

## Introduction

While metadata quality can be somewhat subjective, there are a number of key principles that can be objectively assessed and should be universally followed throughout DHIS2 implementations. In order to assess meatadat quakity, a metadat assessment can be performed. In this context, we can define metadata assessment as the review of the quality of a specific implementations configuration. While this is wide-ranging in scope, it our goal to break down the assessment process into manageable pieces that can be reviewed, priortized and fixed over time. Regular metadata assessment and ongoing upkeep is an important part of long-term DHIS2 configuration strategies. While configuration tasks can often be performed quickly through a number of different mechanisms, without proper co-ordination there can be a number of challenges that a DHIS2 systems configuration can face over time. Some examples of the effects of these configuration challenges include:

- An inability to find the correct items when creating data outputs
- An inability to correctly disaggregate data when creating data outputs
- An inability to access the correct items when either entering data or creating data outputs
- Challenges with data quality (some examples: significant inaccuracies in long term trends of data and reporting rates, being able to store invalid data values, multiple variables representing the same concept storing different data values)
- Difficulty identifying the correct items to use when configuring data exchange mechanisms  
- Errors when upgrading DHIS2 versions
- Having an overwhelming amount of invalid metadata to manage

The purpose of this guide is to help identify the various root causes that can result in poor configuration practices as well as providing tools and procedures which can support both immediate fixes as well as long-term strategies to modify these practices over time. As DHIS2 implementations develop over time and grow into increasingly larger data warehouses, implementation of such interventions will prove beneficial to the ongoing long-term sustainbility and usability of the platform. 

This guide is broken down into the following sections:

- **Metadata Assessment Checklist:** provides you with a detailed checklist of items that should be checked when performing a review of the meta-data in the system. These checklist is broken down into 3 types of checks that can be performed:
  - Data Integrity Check : This is built directly into DHIS2 and can be run via the data administration app
  - Scripts : The checklist for scripts highlights areas of DHIS2 configuration that can not be assessed via the data integrity check
  - Manual Processes : There are some items in which a manual review will need to be performed


-  **Metadata Assessment Reference Guide:** describes in detail each item that is included within the checklist. Each item on the checklist will have the following accompanying text available within the metadata assessment reference guide:
   -  A description of the item and why it should be checked
   -  Instructions on tools or processes you can use to assess whether or not the item is problematic
   -  Instructions on tools or processes that can be used to fix the item if it is identified as problematic
   -  Best practice recommendations to implement pro-active measures to handle the item in the future


-  **Procedures for long-term maintenance:** describes procedural challenges associated with co-ordinating long-term configuraion processes and provides example standard operating procedures that can be reviewed and used to better co-ordinate these processes

## Performing the Assessment

In order to perform the assessment, you may want to start by getting buy-in from a wide variety of stakeholders. In doing so, it may be useful to document the extent of the issues discussed within this guide by generating summary statistics on the problems that can been identified. This can be very useful to present to a large audience and can be used to support buy-in by providing brief explanations of the issues that have been identified. Within the **Metadata Assessment Reference Guide** you will find tools that will support you to both create quick summary counts of problems that you find in your own implementation as well as tools that generate more detailed reports on each specific item that requires attention. We recommend that the assessment includes the following components:


1. Defing the scope of the assessment and sharing this with relevant stakeholders
2. Identifying the extent of the problems within an implementation through generating and documenting summary statistics of what has been found
3. Presenting these findings back to the group of stakeholders
4. Identifying the individual items that are problematic and coming up with strategies to mitigate or fix them as appropriate
5. Detailing and priortizing the fixes
6. 
