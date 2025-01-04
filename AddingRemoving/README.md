# Adding and Removing Rows and Columns in pandas

In pandas, manipulating rows and columns in a DataFrame is essential for data analysis and preprocessing. Below are examples of adding and removing rows and columns using practical examples.

---

## Adding a New Column
You can create new columns by combining or transforming existing columns. For example:

```python
# Add a 'full_name' column by concatenating 'first' and 'last' columns
df['full_name'] = df['first'] + ' ' + df['last']
```

### Explanation
- The `+` operator concatenates the values in the `first` and `last` columns, separated by a space (`' '`).

---

## Removing Columns
To remove columns from the DataFrame, use the `drop` method.

```python
# Drop the 'first' and 'last' columns from the DataFrame
df.drop(columns=['first', 'last'], inplace=True)
```

### Explanation
- `columns=['first', 'last']`: Specifies the columns to be removed.
- `inplace=True`: Ensures the changes are applied to the original DataFrame.

---

## Splitting a Column into Multiple Columns
You can split a column into multiple columns using the `str.split` method:

```python
# Split the 'full_name' column into 'first' and 'last' columns
df[['first', 'last']] = df['full_name'].str.split(' ', expand=True)
```

### Explanation
- `str.split(' ')`: Splits the string in the `full_name` column by spaces.
- `expand=True`: Ensures the result is a DataFrame that can be assigned to new columns.

---

## Adding Rows to the DataFrame
To add new rows, you can use `pd.concat` with another DataFrame:

### Example 1: Adding a Single Row
```python
new_row = pd.DataFrame([{'first': 'Tony'}])
df = pd.concat([df, new_row], ignore_index=True)
```

### Example 2: Adding Multiple Rows from Another DataFrame
```python
df = pd.concat([df, df2], ignore_index=True)
```

### Explanation
- `pd.concat([df, new_row], ignore_index=True)`: Combines `df` with `new_row` and resets the index.
- You can also concatenate another DataFrame (`df2`) to append multiple rows.

---

## Removing Rows
You can remove rows based on a condition by using the `drop` method.

```python
# Filter rows where 'last' is 'Doe'
filt = df['last'] == 'Doe'

# Drop the filtered rows
df = df.drop(index=df[filt].index)
```

### Explanation
- `df['last'] == 'Doe'`: Creates a filter for rows where the `last` column has the value `'Doe'`.
- `df[filt].index`: Gets the index of rows to be dropped.
- `drop(index=...)`: Removes the specified rows.

---

## Summary
These techniques are crucial for data manipulation and allow for efficient and flexible operations:

1. **Adding Columns**:
   - Combine or transform existing columns.
2. **Removing Columns**:
   - Use `drop` to remove unwanted columns.
3. **Splitting Columns**:
   - Use `str.split` to split a column into multiple columns.
4. **Adding Rows**:
   - Use `pd.concat` to append single or multiple rows.
5. **Removing Rows**:
   - Filter and drop rows based on conditions.

Mastering these operations will streamline your data preprocessing workflow!
