# Ride Booking Data Cleaning

## Project Overview

This project focuses on cleaning and documenting a real-world ride booking dataset using Python and Pandas. The objective is to identify and handle missing values, duplicate records, incorrect data types, unusable columns, redundant information, and inconsistent data while keeping the original dataset unchanged.

## Dataset

The dataset contains ride booking records with information about booking status, customer and vehicle details, locations, cancellation information, payment methods, booking values, ride distance, and ratings.

The original raw dataset is stored in:

`data/raw/Bookings.csv`

The raw file is kept unchanged throughout the project.

## Tools and Technologies

- Python
- Pandas
- Jupyter Notebook
- VS Code
- Git
- GitHub

## Dataset Statistics

### Before Cleaning

- Rows: 103,024
- Columns: 21

### After Cleaning

- Rows: 103,024
- Columns: 18

### Rows Removed

- Duplicate rows removed: 0
- Duplicate Booking IDs removed: 0
- Other rows removed: 0

No rows were removed because the missing values were mainly associated with booking situations where certain information was not applicable.

## Cleaning Performed

### Date

The `Date` column was converted from object/string format to `datetime64[ns]`.

### Removed `Unnamed: 20`

The column contained 103,024 missing values and therefore contained no usable information.

### Removed `Vehicle Images`

All 103,024 values contained `#NAME?`, so the column was removed because it contained invalid and unusable information.

### Removed `Time`

The `Time` column exactly matched the time component of the `Date` column for all 103,024 records. It was therefore redundant.

### Missing Cancellation Information

Missing values in cancellation-related columns were replaced with `Not Applicable` where the information did not apply to the booking.

### Missing Payment Method

The 39,057 missing payment methods corresponded to non-successful bookings. These values were replaced with `Not Applicable`.

### Missing Ratings and TAT Values

Missing `V_TAT`, `C_TAT`, `Driver_Ratings`, and `Customer_Rating` values were retained as missing because these measurements were not applicable to unsuccessful bookings.

### Duplicate Checking

No complete duplicate rows were found.

No duplicate `Booking_ID` values were found.

### Numerical Validation

The following invalid-value checks found zero invalid records:

- V_TAT <= 0: 0
- C_TAT <= 0: 0
- Booking Value <= 0: 0
- Ride Distance < 0: 0
- Driver Rating outside 3–5: 0
- Customer Rating outside 3–5: 0

### Category Validation

The categorical columns were checked for leading and trailing whitespace. No values with extra whitespace were found.

## Project Structure

```text
ride-booking-data-cleaning/
│
├── data/
│   ├── raw/
│   │   └── Bookings.csv
│   │
│   └── cleaned/
│       └── cleaned_bookings.csv
│
├── notebooks/
│   └── ride_booking_cleaning.ipynb
│
├── docs/
│   └── cleaning_decisions.md
│
├── .gitignore
└── README.md

## Task 2: Exploratory Analysis and Visual Summary

Task 2 analyzes the cleaned ride booking dataset produced in Task 1. The analysis focuses on trip volume, revenue, peak booking hours, city-wise usage, and driver ratings.

### Analysis Performed

The notebook performs the following analysis:

- Ride bookings by hour
- Ride bookings over time
- Successful booking value by pickup location
- Ride bookings by pickup location
- Driver rating distribution by vehicle type

### Visualizations

Five charts are generated and saved as PNG files:

1. `trips_by_hour.png` — booking volume by hour
2. `trips_over_time.png` — booking volume over time
3. `revenue_by_city.png` — successful booking value by pickup location
4. `city_wise_usage.png` — booking volume by pickup location
5. `driver_rating_heatmap.png` — driver rating distribution by vehicle type

### Python Packages

The project uses:

- Python 3
- pandas
- matplotlib
- seaborn
- Jupyter

Install the required packages with:

```bash
pip install pandas matplotlib seaborn jupyter