# Filtering in Pandas

Pandas is a powerful Python library for data manipulation and analysis. Filtering is one of the core functionalities in pandas, allowing users to select rows of a DataFrame based on specific conditions.

## What is Filtering?

Filtering in pandas involves extracting subsets of data from a DataFrame that meet one or more conditions. This is particularly useful for analyzing or transforming data efficiently.

---

## How Does It Work?

Pandas filtering uses boolean indexing to select rows based on one or multiple conditions. You can specify the conditions using logical operators like:

- `&` (AND)
- `|` (OR)
- `~` (NOT)

The filtering process generates a boolean mask (a series of `True` or `False` values), which is then applied to the DataFrame to extract rows where the condition is `True`.

---

## Syntax

```python
filtered_data = df[condition]
```

OR

```python
filtered_data = df.loc[condition, columns_to_select]
```

### Example

Given the following DataFrame:

```python
import pandas as pd

data = {
    "first": ["Kiyo", "Jane", "John"],
    "last": ["Ndux", "Doe", "Doe"],
    "email": ["rmvilla987@gmail.com", "JaneDoe@email.com", "JohnDoe@email.com"]
}

df = pd.DataFrame(data)
```

#### DataFrame:
| first | last  | email                  |
|-------|-------|------------------------|
| Kiyo  | Ndux  | rmvilla987@gmail.com  |
| Jane  | Doe   | JaneDoe@email.com     |
| John  | Doe   | JohnDoe@email.com     |

### Filtering Examples

1. **Filter by Multiple Conditions**:
   To filter rows where `last` is "Doe" and `first` is "John":

   ```python
   filt = (df['last'] == 'Doe') & (df['first'] == 'John')
   result = df.loc[filt, 'email']
   print(result)
   ```

   **Output**:
   ```
   2    JohnDoe@email.com
   Name: email, dtype: object
   ```

2. **Filter by OR Condition**:
   To filter rows where `last` is "Ndux" or `first` is "John":

   ```python
   filt = (df['last'] == 'Ndux') | (df['first'] == 'John')
   result = df.loc[filt, 'email']
   print(result)
   ```

   **Output**:
   ```
   0    rmvilla987@gmail.com
   2    JohnDoe@email.com
   Name: email, dtype: object
   ```

3. **Negate a Condition**:
   To exclude rows where `first` is "Jane":

   ```python
   filt = ~df['first'].str.contains('Jane')
   result = df.loc[filt, 'email']
   print(result)
   ```

   **Output**:
   ```
   0    rmvilla987@gmail.com
   2    JohnDoe@email.com
   Name: email, dtype: object
   ```

---

## Benefits of Filtering

- **Quick Data Exploration**: Easily analyze subsets of data.
- **Efficiency**: Faster and more concise than looping through data manually.
- **Scalability**: Handles large datasets seamlessly.

---

## Additional Tips

- Use parentheses to group conditions when combining them with `&` or `|`.
- Use `.loc` for more explicit indexing and selection.
- Ensure column names used in conditions are correctly spelled to avoid errors.
