# Near-Earth Object Hazard Classification

## Project Overview

This project investigates whether near-Earth objects (**NEO**s) can be classified as potentially hazardous using their physical and orbital characteristics.

The analysis combines a large primary NEO dataset with supplementary orbital information, explores differences between hazardous and non-hazardous objects, and compares two machine-learning approaches: **Logistic Regression** and a **Simplified Random Forest**.

The final model recommendation prioritises **recall**, because failing to identify a hazardous object was treated as a more serious error than incorrectly flagging a non-hazardous object.

## Project Question

Can Logistic Regression and Random Forest models **classify potentially hazardous near-Earth objects** using their physical and orbital characteristics, and **which approach is most suitable** when minimising missed hazardous objects is the priority?

## Tools Used

- Python
- pandas
- matplotlib
- scikit-learn
- Jupyter Notebook
- Power BI
- GitHub

## Data Sources

Two datasets were used in this project:

- A primary near-Earth object dataset containing physical characteristics such as absolute magnitude, estimated diameter, relative velocity, miss distance and the hazardous classification.
- A supplementary dataset containing orbital characteristics including eccentricity, semi-major axis, perihelion distance, orbital inclination, orbital period and orbit class.

The datasets were linked using the NEO identifier. Of the **338,171** cleaned primary records, **241,900** matched to the supplementary dataset, giving a match rate of **71.53%**.

The unmatched records were investigated rather than automatically discarded. Their hazardous-object rate differed from the matched records, indicating that removing them through an inner join could introduce selection bias. A **left join** was therefore used to retain all primary records while adding orbital information where available.

## Data Engineering & Quality

The primary dataset was cleaned by checking for missing values and duplicate records. Only **28** rows contained missing values in key physical characteristics, so these were removed, leaving **338,171 records** for analysis.

Data quality was considered using the **UK Government Data Quality Framework**, with particular attention to completeness, uniqueness, validity and consistency.

- **Completeness:** missing values and supplementary-data coverage were assessed.
- **Uniqueness:** duplicate records and identifier uniqueness were checked before joining.
- **Validity:** data types and numerical distributions were reviewed to identify unexpected values.
- **Consistency:** identifier matching and row counts before and after the join were checked to ensure the integration process did not remove or multiply primary records.

The supplementary dataset was joined to the primary dataset using a **left join**. This preserved all cleaned primary NEO records while adding orbital information where a match was available.

**Accuracy** could not be independently verified from the supplied datasets alone, while **timeliness** was less important because the project focused on historical NEO observations.
