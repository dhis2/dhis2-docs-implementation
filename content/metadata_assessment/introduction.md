# Introduction

Regular metadata assessment and ongoing upkeep is an important part of long-term DHIS2 configuration strategies. While configuration tasks can often be performed quickly through a number of different mechanisms, without proper co-ordination there can be a number of challenges that a DHIS2 systems configuration can face over time. Some examples include:

- An inability to find the correct items when creating data outputs
- An inability to correctly disaggregate data when creating data outputs
- An inability to access the correct items when either entering data or creating data outputs
- Challenges with data quality (some examples: significant inaccuracies in long term trends of data and reporting rates, being able to store invalid data values, multiple variables representing the same concept stored with different values)
- Difficulty identifying the correct items to use when configuring data exchange mechanisms  
- Errors when upgrading DHIS2 versions
- Having an overwhelming amount of invalid metadata to manage

The purpose of this guide is to help identify the various root causes that can result in poor configuration practices as well as providing tools and procedures which can support both immediate fixes as well as long-term strategies to modify these practices over time. As DHIS2 implementations develop over time and grow into increasingly larger data warehouses, implementation of such interventions will prove beneficial to the ongoing long-term sustainbility and usability of the platform. 

This guide is broken down into the following sections:

- **Metadata Assessment Checklist:** provides you with a detailed checklist of items that should be checked when performing a review of the meta-data in the system. 
-  **Metadata Assessment Reference Guide:** describes in detail each item that is included within the checklist. Each item on the checklist will have the following accompanying text available within the metadata assessment reference guide:
   -  A description of the item and why it should be checked
   -  Instructions on tools or processes you can use to assess whether or not the item is problematic
   -  Instructions on tools or processes that can be used to fix the item if it is identified as problematic
   -  Best practice recommendations to implement pro-active measures to handle the item in the future
-  **Procedures for long-term maintenance:** describes procedural challenges associated with co-ordinating long-term configuraion processes and provides example standard operating procedures that can be reviewed and used to better co-ordinate these processes


