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
Task 2: Exploratory Analysis and Visual Summary
Task 2 uses the cleaned CSV produced in Task 1 to explore ride booking patterns and generate business-oriented visualizations.
The analysis focuses on:
- Trip volume
- Revenue
- Peak booking hours
- City-wise usage
- Driver ratings
Analysis Performed
The Task 2 notebook performs the following analysis:
- Ride bookings by hour
- Ride bookings over time
- Successful booking value by pickup location
- Ride bookings by pickup location
- Driver rating distribution by vehicle type
Pandas groupby() is used to aggregate bookings and booking values, while Matplotlib and Seaborn are used to create the visualizations.
Task 2 Notebook
The Task 2 exploratory analysis notebook is located at:
notebooks/ride_booking_analysis.ipynb
The notebook loads the cleaned dataset from:
data/cleaned/cleaned_bookings.csv
A reusable load_cleaned_data() function is included in the notebook to load the cleaned data and prepare the Date column for time-based analysis.
Visualizations
Five charts are generated and saved as PNG files:
1. trips_by_hour.png — booking volume by hour
2. trips_over_time.png — booking volume over time
3. revenue_by_city.png — successful booking value by pickup location
4. city_wise_usage.png — booking volume by pickup location
5. driver_rating_heatmap.png — driver rating distribution by vehicle type
The generated charts are stored in:
outputs/charts/
Business Analysis
The exploratory analysis provides business-relevant information about:
- Peak periods of ride demand
- Changes in booking volume over time
- Booking activity across pickup locations
- Successful booking value across locations
- Driver rating distribution across vehicle types
These findings can help RapidRide understand customer demand patterns and support decisions related to driver scheduling, vehicle allocation, and service-quality monitoring.
How to View and Run the Notebooks
View the Notebook in VS Code
The notebooks can be viewed directly in Visual Studio Code.
Steps
1. Clone or download this GitHub repository.
2. Open the project folder in VS Code.
3. Open the notebooks folder.
4. Open ride_booking_cleaning.ipynb to view the Task 1 cleaning analysis.
5. Open ride_booking_analysis.ipynb to view the Task 2 exploratory analysis.
6. If VS Code asks you to select a Python kernel, select an installed Python environment.
7. The notebook will open in the VS Code Notebook interface.
8. To execute the complete notebook, use the Run All option in the notebook toolbar.
View the Notebook Using Jupyter Notebook
Jupyter Notebook can also be used to view and run the notebooks.
Open a terminal in the project folder and run:
jupyter notebook

A browser window will open.
Navigate to the notebooks folder and select either:
ride_booking_cleaning.ipynb

or:
ride_booking_analysis.ipynb

The notebook can then be viewed and executed from the Jupyter Notebook interface.
Run the Task 2 Analysis
After opening:
notebooks/ride_booking_analysis.ipynb
run the notebook from the first cell to the last cell.
The notebook will:
1. Load the cleaned dataset.
2. Prepare the date information.
3. Analyze trip volume.
4. Analyze peak booking hours.
5. Analyze booking value.
6. Analyze city-wise usage.
7. Analyze driver ratings.
8. Generate the visualizations.
9. Save the charts as PNG files.
The generated charts will be saved in:
outputs/charts/
Project Structure
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
│   ├── ride_booking_cleaning.ipynb
│   └── ride_booking_analysis.ipynb
│
├── outputs/
│   └── charts/
│       ├── trips_by_hour.png
│       ├── trips_over_time.png
│       ├── revenue_by_city.png
│       ├── city_wise_usage.png
│       └── driver_rating_heatmap.png
│
├── docs/
│   └── cleaning_decisions.md
│
├── src/
│
├── .gitignore
│
└── README.md
# Ride Booking Data Cleaning and Exploratory Analysis

## Project Overview

This project focuses on cleaning and documenting a real-world ride booking dataset using Python and Pandas. The objective is to identify and handle missing values, duplicate records, incorrect data types, unusable columns, redundant information, and inconsistent data while keeping the original dataset unchanged.

The project also includes exploratory analysis of the cleaned ride booking data. The analysis examines trip volume, revenue, peak booking hours, city-wise usage, and driver ratings using Python, Pandas, Matplotlib, and Seaborn.

## Dataset

The dataset contains ride booking records with information about booking status, customer and vehicle details, locations, cancellation information, payment methods, booking values, ride distance, and ratings.

The original raw dataset is stored in:

`data/raw/Bookings.csv`

The raw file is kept unchanged throughout the project.

The cleaned dataset is stored in:

`data/cleaned/cleaned_bookings.csv`

## Tools and Technologies

- Python
- Pandas
- Matplotlib
- Seaborn
- Jupyter Notebook
- VS Code
- Git
- GitHub

## Required Python Packages

The following Python packages are required to run the notebooks:

- pandas
- matplotlib
- seaborn
- jupyter

Install the required packages using:

```bash
pip install pandas matplotlib seaborn jupyter

Reproducibility
The raw dataset is kept untouched in data/raw/.
The cleaned dataset is stored separately in data/cleaned/.
The Task 1 notebook documents the cleaning process, while the Task 2 notebook loads the cleaned dataset using the load_cleaned_data() function.