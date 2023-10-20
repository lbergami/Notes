# Data Warehouse summary notes 

&nbsp;

## Data Warehousing general concepts 

* DB and WH are not the same thing. A DW is written on top of a DB, so *usage* Vs *platform*.
  
* DW are useful for two reasons:
    * Data once transformed are available to support data-driven decisions.
    * One-stop shopping: data are integrating in one location
      
* There are a few rules to follow when we build a DW.

&nbsp;

## Data Warehouse architecture 


1. **Centralized DW Vs Component-based DW**

* Two different approaches to a DW architecture

| centralized DW | component-based DW |
| -------- | ------- |
| Default option | Overcome org challenges but more complext to cross integrate different components |
| One-stop shopping: Single DW where all your data sources feed in  | It may create inconsistencies across data  |
| Lower data governace efforts | 
| More appropriate for Big Data | 


2. **ETL Vs ELT**

* The difference between the two workflows is the order of the transformation.
    * ETL (traditional): data are loaded in their finished and transformed state
    * ELT: Transformation capacity is increased, exploiting cloud platform. You are not committed to the hardware footprint

 
3. **Staging**

  * First stop of a DW and landing zone of data sources. The staging layer feeds into user access layer in a form that is accessible for further work.

  * Staging has one-to-one relationship with data sources (which may come from different vendors)
    
  * Staging can be persistent Vs non-persistent (data stage layers are erased when are added to the user access layer), i.e. less storage space but potential data quality issues

  *  Source data may need to be refreshed: new data, modified data, delete data. There are different approaches ( The first two are the most common):
      * Append pattern: Append on top
      * In-place update: Changing only existing rows 
      * Complete replacement
      * Rolling append: Set out a time window and those observations that are outside that are dropped
   

4. **Data Transformation**

* Data transformation is a key part of the process: it is the intermediate step which make sure that data are uniform across the different sources and amend possible inconsistencies

* Most common transformations are:
    * Data value unification (e.g. country full name and code)
    * Data type and unifications
    * Deduplications
    * Vertical and horizontal slicing when only certain information is relevant for analytical purposes
    * Correct potential known errors
 
5. **Data warehousing design**

* Data dimensionality refers to organize data by measurements and then filter and group data by context
* In a DW setting, when we talk about measurements, we refer to **facts** and dimensional context as **dimensions** 
    


