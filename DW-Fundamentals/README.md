# Data Warehouse summary notes 



## Data Warehousing general concepts 

* DB and WH are not the same thing. A DW is written on top of a DB, so *usage* Vs *platform*.
  
* DW are useful for two reasons:
    * Data once transformed are available to support data-driven decisions.
    * One-stop shopping: data are integrating in one location
      
* There are a few rules to follow when we build a DW.



## Data Warehouse architecture 


1. Different approach between *centralized DW* Vs *component-based DW*: 


| centralized DW | component-based DW |
| -------- | ------- |
| Default option | Overcome org challenges but more complext to cross integrate different components |
| One-stop shopping: Single DW where all your data sources feed in  | It may create inconsistencies across data  |
| Lower data governace efforts | 
| More appropriate for Big Data | 


2. ETL Vs ELT

* The difference between the two workflows is the order of the transformation.
    * ETL (traditional): data are loaded in their finished and transformed state
    * ELT: Transformation capacity is increased, exploiting cloud platform. You are not committed to the hardware footprint
 
3. Staging

  * First stop of a DW and landing zone of data sources. The staging layer feeds into user access layer in a form that is accessible for further work.

  * Staging has one-to-one relationship with data sources (which may come from different vendors)
    
  * Staging can be persistent Vs non-persistent (data stage layers are erased when are added to the user access layer), i.e. less storage space but potential data quality issues

  *  


