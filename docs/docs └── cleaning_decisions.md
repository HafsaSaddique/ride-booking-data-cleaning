# Data Cleaning Decisions

## Dataset

Dataset: Ola & Uber Ride Booking & Cancellation Data

Original file: `data/raw/Bookings.csv`

The raw dataset was kept unchanged throughout the cleaning process.

## Row Counts

- Original rows: 103,024
- Duplicate rows found: 0
- Duplicate Booking IDs found: 0
- Rows removed: 0
- Final rows: 103,024

## Column Cleaning

### 1. Removed `Unnamed: 20`

All 103,024 values in this column were missing.

Decision: The column was removed because it contained no usable information.

### 2. Removed `Vehicle Images`

All 103,024 values contained the invalid value `#NAME?`.

Decision: The column was removed because it contained no useful or valid information.

### 3. Removed `Time`

The time component of `Date` matched the `Time` column for all 103,024 records.

Decision: The `Time` column was removed because it duplicated information already contained in the `Date` column.

### 4. Converted `Date`

The `Date` column was originally stored as an object/string.

Decision: It was converted to `datetime64[ns]` so that the date and time could be correctly interpreted and used for analysis.

## Missing Values

### Canceled_Rides_by_Customer

There were 92,525 missing values.

The non-missing values exactly matched the 10,499 bookings with `Booking_Status = Canceled by Customer`.

Decision: Missing values were replaced with `Not Applicable` because the field does not apply when the customer did not cancel the booking.

### Canceled_Rides_by_Driver

There were 84,590 missing values.

The non-missing values exactly matched the 18,434 bookings with `Booking_Status = Canceled by Driver`.

Decision: Missing values were replaced with `Not Applicable` because the field does not apply when the driver did not cancel the booking.

### Incomplete_Rides

There were 39,057 missing values.

These corresponded exactly to the 39,057 non-successful bookings.

Decision: Missing values were replaced with `Not Applicable` because an incomplete-ride status does not apply to bookings that were not successful.

### Incomplete_Rides_Reason

There were 99,098 missing values.

The non-missing reasons corresponded to the 3,926 bookings marked as incomplete.

Decision: Missing values were replaced with `Not Applicable` because no incomplete-ride reason applies when a booking was not marked as incomplete.

### Payment_Method

There were 39,057 missing values.

These corresponded exactly to the 39,057 non-successful bookings.

Decision: Missing values were replaced with `Not Applicable` because no payment method was recorded for bookings that did not result in a successful ride.

### V_TAT and C_TAT

Each contained 39,057 missing values.

These missing values corresponded to non-successful bookings.

Decision: Missing values were retained as `NaN` because these measurements are not applicable to bookings that were not successfully completed. Artificially replacing them with zero or another numeric value would create misleading measurements.

### Driver_Ratings and Customer_Rating

Each contained 39,057 missing values.

These missing values corresponded to non-successful bookings.

Decision: Missing values were retained as `NaN` because ratings are not applicable when a ride was not successfully completed. They were not replaced with artificial rating values.

## Duplicate Checks

No complete duplicate rows were found.

No duplicate `Booking_ID` values were found.

Decision: No records were removed for duplication.

## Category Consistency

The categorical columns were checked for leading or trailing whitespace.

No values with extra whitespace were found.

Decision: No category formatting changes were required.

## Numerical Validation

The following checks found no invalid values:

- V_TAT less than or equal to zero: 0
- C_TAT less than or equal to zero: 0
- Booking_Value less than or equal to zero: 0
- Ride_Distance below zero: 0
- Driver ratings outside 3–5: 0
- Customer ratings outside 3–5: 0

## Zero Ride Distance

There were 39,057 records with zero ride distance.

All 39,057 belonged to non-successful bookings, while no successful booking had zero ride distance.

Decision: Zero values were retained because they are consistent with bookings that did not result in a completed ride.

## Final Result

- Original rows: 103,024
- Final rows: 103,024
- Original columns: 21
- Final columns: 18
- Rows removed: 0
- Columns removed: 3