
# CSV Filter and Pagination Function

## Overview
This project provides a function to read a CSV file and return rows that match given filter criteria, similar to SQL `WHERE` conditions. The function supports complex nested conditions and paginates the results into pages of size 50.

## Features
- **Filter Expression Parsing:** Parses complex nested filter expressions.
- **Row Filtering:** Filters rows based on the parsed filter expression.
- **Pagination:** Supports pagination to handle large CSV files.
- **Binary Operators:** Supports binary operators (AND, OR).

## Constraints
- The CSV file may contain millions of rows.
- The filter expression can be a complex nested condition.
- Example filter expression: `(((column_name = "practo") AND (column_name != "dogreat")) OR (column_name <= 100))`.

## Scoring Criteria
- **Function Signature (20%)**
- **File Reader (20%)**
- **Filter Expression Evaluator (20%)**
- **Pagination (20%)**
- **Full Working Solution (20%)**

## Solution
The solution is provided in the `sol.py` file.

### Function Signature
```sh
def read_csv_with_filter(file_path, filter_criteria, page_number=1, page_size=50):
```

### File Reader
Uses the `csv` module to read the CSV file.

### Filter Expression Evaluator
Uses the `ast` module to parse and evaluate filter expressions.

### Pagination
Paginates the results into pages of size 50.

## Usage
### Example Usage
```python
file_path = 'data.csv'
filter_criteria = '((department == "Engineering") AND (age != 45)) OR (salary <= 60000)'
page_number = 1
page_size = 50

rows = read_csv_with_filter(file_path, filter_criteria, page_number, page_size)
for row in rows:
    print(row)
```

### Additional Examples
#### Example 1: Large CSV File
```python
file_path = 'large_sample.csv'
filter_criteria = '((department == "Engineering") OR (department == "Sales")) AND (age < 35)'

page_number = 1
page_size = 50

rows = read_csv_with_filter(file_path, filter_criteria, page_number, page_size)
for row in rows:
    print(row)
```

#### Example 2: Filter by Department and Age Range
```python
filter_criteria = '(department == "Marketing") AND (age >= 30) AND (age <= 40)'
rows = read_csv_with_filter(file_path, filter_criteria, page_number, page_size)
print("Filter by Department and Age Range:")
for row in rows:
    print(row)
```

#### Example 3: Filter by Salary and Exclude a Specific Department
```python
filter_criteria = '(salary > 70000) AND (department != "HR")'
rows = read_csv_with_filter(file_path, filter_criteria, page_number, page_size)
print("Filter by Salary and Exclude a Specific Department:")
for row in rows:
    print(row)
```

#### Example 4: Filter by Multiple Departments and Age
```python
filter_criteria = '((department == "Engineering") OR (department == "Sales")) AND (age < 35)'
rows = read_csv_with_filter(file_path, filter_criteria, page_number, page_size)
print("Filter by Multiple Departments and Age:")
for row in rows:
    print(row)
```

#### Example 5: Filter by Name Length and Salary Range
```python
filter_criteria = '(len(name) > 8) AND (salary >= 50000) AND (salary <= 100000)'
rows = read_csv_with_filter(file_path, filter_criteria, page_number, page_size)
print("Filter by Name Length and Salary Range:")
for row in rows:
    print(row)
```

#### Example 6: Filter by Exact Name and Department
```python
filter_criteria = '(name == "John Doe") AND (department == "Engineering")'
rows = read_csv_with_filter(file_path, filter_criteria, page_number, page_size)
print("Filter by Exact Name and Department:")
for row in rows:
    print(row)
```

#### Example 7: Complex Nested Conditions
```python
filter_criteria = '((department == "Support") AND (age >= 25) AND (age <= 50)) OR ((salary < 60000) AND (department != "Marketing"))'
rows = read_csv_with_filter(file_path, filter_criteria, page_number, page_size)
print("Complex Nested Conditions:")
for row in rows:
    print(row)
```

## Data Files
### `data.csv`
```plaintext
id,name,age,salary,department
1,John Doe,28,55000,Engineering
2,Jane Smith,34,75000,Marketing
3,Alice Johnson,23,48000,HR
4,Chris Lee,45,92000,Engineering
5,Eva Brown,29,60000,Marketing
6,Mike Davis,50,100000,HR
7,Anna Wilson,32,68000,Engineering
8,James Taylor,41,80000,Marketing
9,Emily Clark,27,54000,HR
10,Michael Johnson,36,78000,Engineering
```

### `large_sample.csv`
```plaintext
id,name,age,salary,department
1,addolcBPOt,52,70692,Sales
2,lTpHyxYbIG,56,51753,Marketing
3,LnTqslHQyQ,37,71400,Engineering
4,vnO peNBZC,47,98974,Engineering
5,OiWmtPNnMr,42,85136,HR
...
```

## Installation
1. Clone the repository.
2. Ensure you have Python 3.x installed.
3. Run the script using `python sol.py`.
