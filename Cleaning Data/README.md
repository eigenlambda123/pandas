# Cleaning Data in pandas

Data cleaning is an essential part of data analysis to ensure data accuracy, consistency, and reliability. The following examples demonstrate common data cleaning techniques using pandas.

## Replacing Missing or Placeholder Values
Replace specific values in the DataFrame with `NaN` (Not a Number):
```python
# Replace specific placeholders with NaN
df.replace('NA', np.nan, inplace=True)
df.replace('Missing', np.nan, inplace=True)
```

## Defining Custom Missing Value Identifiers
Define custom missing value identifiers when reading a CSV file:
```python
# Specify custom NA values
na_vals = ['NA', 'Missing']
df = pd.read_csv('data/survey_results_public.csv', index_col='ResponseId', na_values=na_vals)
```

## Dropping Rows with Missing Data
Drop rows with missing values based on specific columns:
```python
# Drop rows where all values in the specified columns are NaN
df.dropna(axis='index', how='all', subset=['last', 'email'])
```

## Checking for Missing Values
Check where values are `NaN`:
```python
# Check for NaN values
df.isna()
```

## Filling Missing Values
Fill missing values with a placeholder or default value:
```python
# Fill missing values with a placeholder
df.fillna('MISSING')
```

## Handling Unique and Inconsistent Values
Identify and handle unique or inconsistent values in a column:
```python
# Check unique values in the column
df['YearsCode'].unique()

# Replace inconsistent string values with numerical values
df['YearsCode'].replace('Less than 1 year', 0, inplace=True)
df['YearsCode'].replace('More than 50 years', 51, inplace=True)
```

## Changing Data Types
Convert a column to a specific data type after cleaning:
```python
# Convert the column to a float
df['YearsCode'] = df['YearsCode'].astype(float)
```

---

### Summary
The above examples show how to:
1. Replace placeholders or invalid values.
2. Define custom missing value identifiers when loading data.
3. Drop rows with missing values selectively.
4. Inspect and fill missing values.
5. Handle inconsistent values and convert data types for better analysis.
