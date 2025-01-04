# Sorting Data in pandas

Sorting data in pandas allows you to organize your DataFrame or Series by rows or columns based on specific criteria. Below are various examples and explanations of sorting techniques.

---

## Sorting Rows by Column Values

### Example 1: Sorting by a Single Column
```python
df.sort_values(by='last')
```

### Explanation
- `by='last'`: Specifies the column (`last`) to sort by.
- By default, the sorting is in ascending order.

---

### Example 2: Sorting by Multiple Columns
```python
df.sort_values(by=['last', 'first'], ascending=False)
```

### Explanation
- `by=['last', 'first']`: Specifies multiple columns for sorting. The `last` column is sorted first, followed by the `first` column.
- `ascending=False`: Sorts all specified columns in descending order.

---

### Example 3: Sorting by Multiple Columns with Mixed Order
```python
df.sort_values(by=['last', 'first'], ascending=[False, True], inplace=True)
```

### Explanation
- `ascending=[False, True]`: Specifies descending order for `last` and ascending order for `first`.
- `inplace=True`: Modifies the DataFrame directly without creating a new one.

---

## Sorting by Index
To sort the rows by their index, use `sort_index`:

```python
df.sort_index()
```

### Explanation
- `sort_index()`: Sorts the DataFrame by its row index in ascending order.

---

## Sorting a Single Column
You can sort a specific column in isolation:

```python
df['last'].sort_values()
```

### Explanation
- `sort_values()`: Sorts the values in the `last` column in ascending order.
- Returns a Series of sorted values.

---

## Finding the Largest or Smallest Values

### Example 1: Finding the Top N Largest Values
```python
df['CompTotal'].nlargest(10)
```

### Explanation
- `nlargest(10)`: Returns the 10 largest values in the `CompTotal` column.

---

### Example 2: Finding the Top N Smallest Values
```python
df.nsmallest(10, 'CompTotal')
```

### Explanation
- `nsmallest(10, 'CompTotal')`: Returns the 10 rows with the smallest values in the `CompTotal` column.

---

## Summary
Sorting data is a fundamental task in data analysis. Here's a quick recap:

1. **Sorting Rows by Column Values**:
   - Use `sort_values()` to sort by one or multiple columns.
   - Control the order using `ascending` and `inplace`.

2. **Sorting by Index**:
   - Use `sort_index()` to sort rows based on their index.

3. **Sorting a Single Column**:
   - Use `sort_values()` directly on a Series to sort its values.

4. **Finding Extremes**:
   - Use `nlargest()` and `nsmallest()` to find the top or bottom N values in a column.

Mastering these sorting techniques will help you efficiently organize and analyze your data!
