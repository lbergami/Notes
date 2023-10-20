# Data Warehouse fundamentals summary notes 

<p> <br>

## Data Warehousing general concepts 

* DB and WH are not the same thing. A DW is written on top of a DB, so *usage* Vs *platform*.
  
* DW are useful for two reasons:
    * Data once transformed are available to support data-driven decisions.
    * One-stop shopping: data are integrating in one location
      
* There are a few rules to follow when we build a DW.

<p> <br>

## Data Warehouse architecture 

**1. Centralized DW Vs Component-based DW**

There are two different approaches to a DW architecture

| centralized DW | component-based DW |
| -------- | ------- |
| Default option | Overcome org challenges but more complext to cross integrate different components |
| One-stop shopping: Single DW where all your data sources feed in  | It may create inconsistencies across data  |
| Lower data governace efforts | 
| More appropriate for Big Data | 

<p> <br>

**2. ETL Vs ELT**

* The difference between the two workflows is the order of the transformation.
    * ETL (traditional): data are loaded in their finished and transformed state
    * ELT: Transformation capacity is increased, exploiting cloud platform. You are not committed to the hardware footprint

<p> <br>
 
**3. Staging**

  * First stop of a DW and landing zone of data sources. The staging layer feeds into user access layer in a form that is accessible for further work.

  * Staging has one-to-one relationship with data sources (which may come from different vendors)
    
  * Staging can be persistent Vs non-persistent (data stage layers are erased when are added to the user access layer), i.e. less storage space but potential data quality issues

  *  Source data may need to be refreshed: new data, modified data, delete data. There are different approaches ( The first two are the most common):
      * Append pattern: Append on top
      * In-place update: Changing only existing rows 
      * Complete replacement
      * Rolling append: Set out a time window and those observations that are outside that are dropped
   
<p> <br>

**4. Data Transformation**

* Data transformation is a key part of the process: it is the intermediate step which make sure that data are uniform across the different sources and amend possible inconsistencies

* Most common transformations are:
    * Data value unification (e.g. country full name and code)
    * Data type and unifications
    * Deduplications
    * Vertical and horizontal slicing when only certain information is relevant for analytical purposes
    * Correct potential known errors

<p> <br>
 
**5. Data warehousing design**

* Data dimensionality refers to organize data by measurements and then filter and group data by context
* In a DW setting, when we talk about measurements, we refer to **facts** and dimensional context as **dimensions**
  
| Facts | Dimensions |
| -------- | ------- |
| Numeric and quantifiable| Context and attributes of facts |
| Measurements and metrics  | Included in dimensional tables  |
| Included in fact tables |
| Facts can be additive, non-additive, semi-additive |

* There are two different approaches to implement facts and dimension data: Star schema Vs Snowflake schema. Star and Snowflake schemas share
  the same dimensions but they are materialized with different dimension table representations  

| Star Schema | Snowfalke Schema |
| -------- | ------- |
| All dimensions along a given hierarchy is one dimension table | Each dimension/dimentional level in its own table |
| Only one level away from the fact table along each hierarchy | One or more levels away from fact tables among each hierarchy |
| Dimension tables organized as a star around fact tables | Dimension tables organized as a snowflake around fact tables |
| Overall fewer database joins | Overall more joins required |
| Primary & foreign key relationships straightforward | Primary & foreign key relationships more complex |
| More storage space required: more repetitive data (denormalized approach) | less storage space required: less repetitive data (normalized approach) |

* Database keys
  * they represent the logical relationships to relate data across different tables.
  * There are two fundamentals key types: (i) *Primary* Vs *Foreign* keys; (ii) *Natural* Vs *Surrogate* keys
    * Primary Key: unique identifier for each row in a BD table. Could be a single column (field) or it may require more than one field
    * Foreign Key: some 'other' table primary key. Used to indicate logical relationship helping data integration and query performances
    * Natural & surrogate keys: Natural keys belong to the source systems, and they travel to the DW with the rest of the data. However, in DW, it is best practice to       use surrogate keysas primary/foreign keys to relate data across tables. Surrogate keys do not have business meaning and they are generated in the DW enviroment.   

<p> <br>

**6. Design facts and dimensions in fact tables and dimension tables**

1. Dimension tables
    * Key DW subject areas that provides context to measurements
    * One-stop shopping for all dimensional subjects
    * In a snowflake schema:
      * 1 table for each level of hierachy
      * Every non-terminal dimension has a primary-surrogate key and a next-higher level primary-surrogate key as a foreign key
      * Every terminal dimension has a primary-surrogate key but not foreign key, since there aren't further dimensions at a higher schema
      
2. Fact tables
    * There are 4 different types of fact tables, each of which is used for different purposes
      | Fact table type | Usage |
      | -------- | ------- |
      | Transaction-grained | Record from a transaction |
      | Periodic snapshot | Track a given measurement at a regular interval  |
      | Accumulating snapshots | Track the progress of a business process through formally defined stages |
      | Factless fact tables | Record the occurrence of a transaction that has no measurements
    
    * It is possible to store two ore more facts in the same table only if the following rules apply:
      1. Facts are avaialble at the same level of granularity (i.e. same level of detail)
      2. Facts occurr simultaneosly 
