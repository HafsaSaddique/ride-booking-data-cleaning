# Ride Booking Data Cleaning

## Project Overview

This project focuses on cleaning and documenting a real-world public ride booking dataset using Python and pandas.

The main objective is to identify and handle data quality issues such as missing values, duplicate records, incorrect data types, and inconsistent categorical values.

The original raw dataset will be preserved without modification, while the cleaned dataset will be stored separately.

## Dataset

The project uses a publicly available ride booking dataset containing information related to ride bookings, including booking status, vehicle type, dates, times, locations, cancellation information, and other booking-related attributes.

The original dataset is stored in the `data/raw/` directory.

## Objectives

* Identify missing values and decide how they should be handled.
* Detect and investigate duplicate records.
* Identify and correct inappropriate data types.
* Identify and standardize inconsistent categorical values.
* Preserve the original raw dataset.
* Create and validate a cleaned dataset.
* Document every important cleaning decision and its justification.

## Tools and Technologies

* Python
* Pandas
* Jupyter Notebook
* Git
* GitHub

## Project Structure

```text
ride-booking-data-cleaning/
│
├── data/
│   ├── raw/
│   │   └── Bookings.csv
│   └── cleaned/
│
├── notebooks/
│
├── src/
│
├── docs/
│
├── .gitignore
└── README.md
```

## Data Cleaning

The dataset will be inspected before any cleaning operations are performed.

The following areas will be investigated:

1. Missing values
2. Duplicate records
3. Data types
4. Inconsistent categorical values
5. Invalid or unexpected values

Cleaning decisions will be based on the characteristics of the actual dataset rather than applying changes without justification.

Detailed cleaning decisions, including the number of affected records and reasons for each decision, will be documented in the project documentation.

## Row Count

The original row count will be recorded before cleaning.

The final row count will be recorded after cleaning.

The difference between the two will be explained and justified.

## Status

**Phase 1: Project setup and dataset preparation**

Data inspection and cleaning will be completed in the next phase.
