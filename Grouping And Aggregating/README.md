# Grouping and Aggregating Data in pandas

Grouping and aggregating data in pandas allows you to analyze and summarize data based on specific categories or groups. Below are various examples and explanations of how to use these functionalities effectively.

---

## Aggregating with Statistical Functions

### Example 1: Finding the Median of a Column
```python
df['CompTotal'].median()
```

### Explanation
- Calculates the median of the `CompTotal` column.

---

### Example 2: Finding the Median Across All Numeric Columns
```python
df.median(numeric_only=True)
```

### Explanation
- Calculates the median for all numeric columns in the DataFrame.

---

### Example 3: Descriptive Statistics
```python
df.describe()
```

### Explanation
- Provides a summary of statistical metrics for numeric columns, including count, mean, median, standard deviation, min, max, and quartiles.

---

## Counting Values

### Example 4: Counting Value Frequencies
```python
df['DevType'].value_counts(normalize=True)
```

### Explanation
- Counts unique values in the `DevType` column.
- `normalize=True`: Returns the relative frequencies as proportions instead of absolute counts.

---

## Grouping Data

### Example 5: Creating a GroupBy Object
```python
country_grp = df.groupby(['Country'])
```

### Explanation
- Groups the DataFrame by the `Country` column.

---

### Example 6: Accessing a Specific Group
```python
country_grp.get_group('Philippines')
```

### Explanation
- Retrieves all rows belonging to the group `Philippines`.

---

## Aggregating Within Groups

### Example 7: Value Counts for a Column in Groups
```python
country_grp['DevType'].value_counts().head(50)
```

### Explanation
- Counts unique values in the `DevType` column for each group.
- Limits the output to the top 50 results.

---

### Example 8: Value Counts for a Specific Group
```python
country_grp['DevType'].value_counts().loc['Philippines']
```

### Explanation
- Retrieves the value counts for the `DevType` column within the `Philippines` group.

---

### Example 9: Normalized Value Counts for a Specific Group
```python
country_grp['DevType'].value_counts(normalize=True).loc['Philippines']
```

### Explanation
- Retrieves the relative frequencies (proportions) of `DevType` for the `Philippines` group.

---

### Example 10: Aggregating with Multiple Functions
```python
country_grp['CompTotal'].agg(['median', 'mean']).loc['Canada']
```

### Explanation
- Computes both the median and mean for `CompTotal` in each group.
- Retrieves the result for the `Canada` group.

---

## Filtering and Applying Custom Functions

### Example 11: Filtering Rows and Counting Specific Values
```python
filt = df['Country'] == 'Philippines'
df.loc[filt]['LanguageHaveWorkedWith'].str.contains('Python').sum()
```

### Explanation
- Filters rows where the `Country` is `Philippines`.
- Counts how many respondents have worked with Python.

---

### Example 12: Applying a Custom Function to Groups
```python
country_grp['LanguageHaveWorkedWith'].apply(lambda x: x.str.contains('Python').sum())
```

### Explanation
- Applies a custom function to each group to count how many respondents in each country have worked with Python.

---

## Combining and Analyzing Results

### Example 13: Creating a Summary DataFrame
```python
python_df = pd.concat([country_respondent, country_uses_python], axis='columns', sort=False)
```

### Explanation
- Combines the number of respondents and the number of Python users for each country into a single DataFrame.

---

### Example 14: Renaming Columns
```python
python_df.rename(columns={'count':'NumRespondents', 'LanguageHaveWorkedWith':'NumKnowsPython'}, inplace=True)
```

### Explanation
- Renames columns for clarity.

---

### Example 15: Calculating Percentages
```python
python_df['PctKnowsPython'] = (python_df['NumKnowsPython']/python_df['NumRespondents']) * 100
```

### Explanation
- Calculates the percentage of respondents in each country who know Python.

---

### Example 16: Sorting Results
```python
python_df.sort_values(by='PctKnowsPython', ascending=False, inplace=True)
```

### Explanation
- Sorts the DataFrame by the `PctKnowsPython` column in descending order.

---

## Summary
Grouping and aggregating data in pandas enables powerful and efficient data analysis. Here's a quick overview:

1. **Aggregations**: Use statistical functions like `median()`, `mean()`, and `describe()` to summarize data.
2. **Value Counts**: Count the frequency of unique values with `value_counts()`.
3. **Grouping**: Use `groupby()` to group data by specific categories.
4. **Custom Functions**: Apply custom operations to each group using `apply()`.
5. **Combining and Analyzing**: Merge and calculate new insights using `concat()`, `rename()`, and calculations.

By mastering these techniques, you can derive meaningful insights from large datasets!
