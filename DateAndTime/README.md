# Dates and Time-Series in Pandas

Time-series data is commonly used in various data analysis scenarios, especially for working with financial, weather, or event-based data. Pandas provides extensive functionality to handle dates and time-series data effectively.

---

## Parsing Dates in a CSV File
To handle date and time values properly, ensure they are parsed as `datetime` objects:

```python
from datetime import datetime
import pandas as pd

d_parser = lambda x: datetime.strptime(x, '%Y-%m-%d %I-%p')
df = pd.read_csv('ETH_1h.csv', parse_dates=['Date'], date_parser=d_parser)
```
- **`parse_dates`**: Automatically parses specified columns as datetime.
- **`date_parser`**: Custom function to parse dates in a specific format.

---

## Extracting Date Components
Use the `.dt` accessor to extract specific date parts:

```python
# Get the day of the week for the first row
print(df.loc[0, 'Date'].day_name())

# Add a new column for day names
df['DayOfWeek'] = df['Date'].dt.day_name()
```
- **`day_name()`**: Returns the name of the day for a specific date.

---

## Date Range Analysis
Determine the range of dates in your dataset:

```python
# Find the minimum and maximum dates
min_date = df['Date'].min()
max_date = df['Date'].max()

# Calculate the duration between the two dates
print(max_date - min_date)
```

---

## Filtering by Date Range
Use logical conditions to filter rows based on date ranges:

```python
filt = (df['Date'] >= pd.to_datetime('2019-01-01')) & (df['Date'] <= pd.to_datetime('2020-01-01'))
filtered_data = df.loc[filt]
```
- **`pd.to_datetime`**: Converts a string into a datetime object for comparison.

---

## Setting Date as the Index
Set the `Date` column as the DataFrame index for time-series operations:

```python
df.set_index('Date', inplace=True)
```
- **Setting the index** enables resampling and time-based indexing.

---

## Resampling Time-Series Data
Aggregate data by specific time intervals:

```python
# Find the maximum 'High' price for each day
highs = df['High'].resample('D').max()

# Get the high for a specific day
print(highs['2020-01-01'])

# Aggregate multiple columns for weekly data
weekly_summary = df.resample('W').agg({
    'Close': 'mean',
    'High': 'max',
    'Low': 'min',
    'Volume': 'sum'
})
```
- **`resample('D')`**: Resamples data to daily frequency.
- **`agg()`**: Allows multiple aggregation functions for different columns.

---

## Summary
Pandas provides powerful tools for working with dates and time-series data, including:
- Parsing dates during data import.
- Extracting components like day names or date ranges.
- Filtering and resampling time-series data.

With these techniques, you can perform robust time-based analysis on your datasets!
