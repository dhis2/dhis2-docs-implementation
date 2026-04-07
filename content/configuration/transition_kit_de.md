# Transition Kit from Old Data Entry App (Legacy App) to New Data Entry App (Aggregate data)

- [Transition Kit from Old Data Entry App (Legacy App) to New Data Entry App (Aggregate data)](#transition-kit-from-old-data-entry-app-legacy-app-to-new-data-entry-app-aggregate-data)
  - [Introduction](#introduction)
  - [Benefits in brief](#benefits-in-brief)
  - [Feature comparison of Old (Legacy App) vs. New App.](#feature-comparison-of-old-legacy-app-vs-new-app)
  - [Feature comparison of Legacy App vs. New App Details with Screenshots](#feature-comparison-of-legacy-app-vs-new-app-details-with-screenshots)
    - [Initial Interface Review](#initial-interface-review)
    - [Option Menu Use/Function](#option-menu-usefunction)
    - [Sections and Filters](#sections-and-filters)
      - [Sections](#sections)
      - [Filters](#filters)
    - [Run Validation](#run-validation)
    - [Data Element Details](#data-element-details)
  - [New Features for Version - 42](#new-features-for-version---42)
    - [Pivot options in aggregate datasets sections](#pivot-options-in-aggregate-datasets-sections)
      - [Default](#default)
      - [Pivot](#pivot)
      - [Move a category to rows](#move-a-category-to-rows)
      - [Content displayed before/after section](#content-displayed-beforeafter-section)
  - [Moving a Dataset from the Legacy (Old App) to the New App](#moving-a-dataset-from-the-legacy-old-app-to-the-new-app)
    - [Review Current Configuration](#review-current-configuration)
    - [Understand Changes](#understand-changes)
    - [Prepare for Migration](#prepare-for-migration)
  - [Limitations of New App](#limitations-of-new-app)
  - [Use cases](#use-cases)
    - [Default form:](#default-form)
    - [Section form](#section-form)


## Introduction

This transition kit is designed to support DHIS2 users and implementers in moving from the legacy aggregate Data Entry app to the New Data Entry App. It provides practical guidance, highlights key differences, and outlines updated workflows to ensure a smooth transition.

The goal is to help users adapt quickly and efficiently to the new interface and functionalities introduced in the latest DHIS2 versions, while maintaining **data quality and reporting continuity**.

## Benefits in brief

1. **Modern and user-friendly interface:** More intuitive layout, improved navigation, and responsive design.
2. **Detailed data element information:** Includes code, data element ID, category option combo ID, and last updated details.
3. **Support for configurable forms**(default, section, and HTML-based).
4. **Offline functionality** (especially via DHIS2 Android).
5. **Enhanced validation and feedback**: Interactive side panels with categorized alerts.
6. **Active development and support:** Unlike the deprecated legacy app, the new app is continuously improved and maintained.
7. **Accessibility enhancements**: Better keyboard navigation and usability for a wider range of users.

## Feature comparison of Old (Legacy App) vs. New App.


| **Features**           | **Old App (Legacy App)**             | **New App**                                                  |
|-------------------------|---------------------------------------|--------------------------------------------------------------|
| **Interface**           | Dataset & Period on right; OU on left | OU, Dataset, Period all selected from persistent top bar     |
| **Menus**               | Top-right corner                     | Options button (includes Help)                               |
| **Sections/Filters**    | Visible after period selection        | Available directly at top bar                                |
| **Data element filter** | Limited to one section at a time      | Global filter across sections; can narrow to one section      |
| **Run validation**      | Button at top right menu; opens popup | Bottom of form; interactive side panel with categorized alerts |
| **Data element details**| Popup window for comments/follow-up   | Inline side panel; comments, audit history, legends available |

## Feature comparison of Legacy App vs. New App Details with Screenshots

###  Initial Interface Review

**New App**: Organisation unit, dataset, and period selected from a persistent top bar. Modern, user-friendly design with improved usability.

    Note: In the new app, the Dataset must be chosen before the Organisation Unit.This order is intentional, it helps filter available organisation units to only those assigned to the selected dataset, reducing user errors during data entry.


**Legacy App**: Organisation Unit on left panel, dataset selected separately. Outdated interface and workflows.

![](images/ER_DE2/image30.png)

### Option Menu Use/Function

![](images/ER_DE2/image33.png)

**New App**
* **Print form with values**: Prints the current data entry form including all entered data values. Useful for reviews, audits, or physical record-keeping.
* **Print empty form**: Prints a blank version of the dataset form. Useful for offline data collection or field distribution.
* **Help:** Opens documentation or guidance related to the Data Entry App. Supports users in understanding the interface and resolving issues.

      Note : The new Help button opens a legend explaining the meaning of cell colors and icons; for example, red indicates an unsaved value.It also lists available keyboard shortcuts, helping users navigate and enter data more quickly.

![](images/ER_DE2/image32.png)

**Legacy App** The Print form and Print blank form button is available at the extreme right top corner.

![](images/ER_DE2/image7.png)

### Sections and Filters

#### Sections

Both are supported with section forms where you can select the section of the form.

**New App:** Sections displayed on the top bar after data set, org unit and period have been selected; 

**Legacy App:**  Section forms only available after selecting the period

**Benefit**: Greater efficiency when working with large/complex forms.

![](images/ER_DE2/image14.png)

>Note
> In the **Legacy App,** the data element filter was limited to one section at a time. This meant that if you wanted to find a data element, you had to first navigate to the specific section where it was located (filtering worked only within that active section).
> 
> In the **New App**, the filter is global across all sections and can be applied to one section at a time. This means you can search for any data element from the top filter bar, and it will display results across the entire form, regardless of which section the element belongs to.
> 
> Additionally, when a specific section is open, the filter can be used to narrow down elements within that section alone. This dual functionality offers flexibility and significantly improves efficiency, especially when working with large or complex forms.


#### Filters

**New App:** The filter is global across all sections and can be applied to one section at a time. This means you can search for any data element from the top filter bar, and it will display results across the entire form, regardless of which section the element belongs to.

Additionally, when a specific section is open, the filter can be used to narrow down elements within that section alone. This dual functionality offers flexibility and significantly improves efficiency, especially when working with large or complex forms.

![](images/ER_DE2/image8.png)
![](images/ER_DE2/image16.png)

**Legacy App:** The data element filter was limited to one section at a time. This meant that if you wanted to find a data element, you had to first navigate to the specific section where it was located (filtering worked only within that active section).

![](images/ER_DE2/image11.png)

### Run Validation

**New App:** Validation results shown in a **side panel**, grouped into categories: High, Medium, Low. Alerts are summarized for easier review.

![](images/ER_DE2/image23.png)

**Legacy App**:The ‘Run Validation’ button is located in the bottom-left corner. When clicked validation results appear in a side panel, grouped into High, Medium, and Low categories, with alerts summarized for easier review. 

    Note: The side panel groups validation alerts by severity. Review High alerts first and use the panel to quickly move between issues without losing their place in the form.

![](images/ER_DE2/image21.png)

### Data Element Details

**New App:** Clicking a data cell shows its details in the lower-left section, with a View Details button. This opens a side panel where users can add comments, mark items for follow-up, and view audit history and legends. Keeping all related information in one place gives a clearer, more organized view of each data item. Hide Details closes the panel.

![](images/ER_DE2/image12.png)
![](images/ER_DE2/image13.png)

**Legacy App:** When a user **double-clicked on a data cell** in the Data Entry app (Aggregate), a **popup window** opened.

This popup allowed users to:

* Enter or edit a value
* Add a comment related to the specific data value
* View or update the last updated date
* See who last edited the value

![](images/ER_DE2/image20.png)

## New Features for Version - 42

### Pivot options in aggregate datasets sections

These pivot tables control how data elements and category option combos are displayed within a section of a dataset.

**Configuring Pivot Options for a Data Set**

1. Open the data set - Navigate to the data set you have created and to which you’ve already assigned data elements.
2. Go to 'Manage Sections' - In the data set settings, click on Manage Sections to organize how your form is structured.
3. Select 'Pivot Options' - Inside the section management view, choose Pivot Options to define how your data will be displayed in analytics.
4. Choose the layout based on your design
5. Configure the pivot options (e.g. whether data elements appear as rows or columns) according to the reporting design and data structure you need.

#### Default
By default, data elements are arranged in rows, while categories (disaggregation dimensions) are displayed in columns.

![](images/ER_DE2/image3.png)      

![](images/ER_DE2/image18.png)

#### Pivot

Categories as rows, data elements as columns
   * Useful when there are **many data elements** and few categories
   * Makes the form **more compact horizontally**
  
  ![](images/ER_DE2/image24.png)

#### Move a category to rows

* It is a hybrid layout
* One category dimension is moved to rows
* It helps to give more control when the dataset is large.

  ![](images/ER_DE2/image35.png)
  ![](images/ER_DE2/image27.png)

#### Content displayed before/after section

You can add HTML-based instructions, notes, or links that appear above or below the section form — useful for guidance or data entry rules.


![](images/ER_DE2/image25.png)
![](images/ER_DE2/image17.png)

## Moving a Dataset from the Legacy (Old App) to the New App

### Review Current Configuration

* Data elements and category combinations
* Custom or section forms (Check if using Java script)
* Validation rules
* Indicators

### Understand Changes

* Interface - The user interface is different 
* Custom forms  - using Java script are no longer supported but HTML is supported
* Section forms -  are supported but can have different style with use of pivot - style options
* Filtering - Improved filter and search feature

### Prepare for Migration

* Redesign custom forms without using Java script
* Re - adjust the section forms
* Test all the forms in New App

## Limitations of New App

| **Limitations**                  | **Alternative/Workaround**                               |
|----------------------------------|-----------------------------------------------------------|
| No JavaScript support in custom forms | Use indicators for calculations and validations for logic checks |
| No enhanced styling               | Use HTML (only simple table layouts)                     |

## Use cases

Below are the practical examples showing how forms behave in the **Legacy Data Entry App** compared to the **New Data Entry App**.

### Default form:

1. Interface
  
   **Legacy App** 
    - Organisation unit selected from left-hand panel; dataset separately
    - Outdated layout, harder to navigate between forms

   **New App** 
   - Organisation unit, dataset, and period all selected from the **persistent top bar**. 
   - Modern, cleaner layout for faster switching.
![](images/ER_DE2/image9.png)
![](images/ER_DE2/image28.png)

1. Organization unit

    **Legacy App**: All OUs displayed, even if the dataset is not assigned (inactive ones appear greyed).

    **New App**: Only OUs assigned to the form are enabled
![](images/ER_DE2/image34.png)
![](images/ER_DE2/image15.png)

1. Error Display:

   **Legacy App**: AError shown in popup messages

   **New App**: Errors displayed inline within the form, with clearer indicators

   ![](images/ER_DE2/image1.png)
   ![](images/ER_DE2/image31.png)

2. Run validation interface

   **Legacy App**: “Run Validation” button in top-right menu; results in a popup.

   **New App**:Validation button at the bottom of the form; results appear in a <strong>side panel</strong>, grouped into <em>High / Medium / Low</em>.

      ![](images/ER_DE2/image21.png)
      ![](images/ER_DE2/image23.png)

### Section form

1. Interface
  
   **Legacy App**: Sections appear only after period selection

   **New App**:Section tabs are visible at the top bar immediately

      ![](images/ER_DE2/image19.png)
      ![](images/ER_DE2/image10.png)

2. Filter section

   **Legacy App**: Filter applies to one section at a time

   **New App**:Global filter across all sections, plus ability to narrow to a single section.
   ![](images/ER_DE2/image19.png)
   ![](images/ER_DE2/image9.png)

3. New features
   * Row/Column Switching for categories (e.g., “Communicable immunizable” dataset section).
   * Not available in Legacy App.
   * Makes large forms easier to read horizontally or vertically.
  ![](images/ER_DE2/image45.png)

