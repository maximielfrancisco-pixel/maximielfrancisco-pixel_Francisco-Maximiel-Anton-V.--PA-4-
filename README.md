# maximielfrancisco-pixel_Francisco-Maximiel-Anton-V.--PA-4-
---

### 1) Problem 1: Visayas Communication DataFrame - Filters students from Visayas under the Communication track and selects the required columns.

```python
import pandas as pd
import matplotlib.pyplot as plt

# Import the ECE Board Exam 2 dataset
ECE = pd.read_excel('board2.xlsx')
ECE

# Calculate Average from the four recorded subject scores
subjects = ['Math', 'GEAS', 'Electronics', 'Communication']
ECE['Average'] = ECE[subjects].mean(axis=1)
ECE

# Filter students whose Hometown is Visayas and whose Track is Communication
VisComm = ECE.loc[
    (ECE['Hometown'] == 'Visayas')&
    (ECE['Track'] == 'Communication'),
    ['Name', 'Gender', 'Math', 'Electronics', 'Average']
]
VisComm

# Display the number of rows in VisComm
len(VisComm)
```

##### Step-by-Step Procedure of Functions:
- `import pandas as pd` → imports the Pandas library and gives it the
shorter name pd.
- `import matplotlib.pyplot as plt` → imports Matplotlib's plotting
functions and gives it the shorter name plt.
- `pd.read_excel('board2.xlsx')` → reads the Excel dataset and stores
it as a DataFrame named ECE.
- `ECE` → displays the complete ECE Board Exam 2 dataset.
- `subjects = [...]` → stores the four subject columns that will be
used to calculate the Average.
- `ECE[subjects].mean(axis=1)` → calculates the mean of Math, GEAS,
Electronics, and Communication for each student.
- `ECE['Average'] = ... `→ adds the calculated values as a new Average
column.
- `ECE.loc[...]` → selects rows and columns using label-based
indexing.
- `(ECE['Hometown'] == 'Visayas')` → keeps only students whose
Hometown is Visayas.
- `(ECE['Track'] == 'Communication')` → keeps only students whose
Track is Communication.
- `&` → combines both filtering conditions so that both conditions
must be true.
- `['Name', 'Gender', 'Math', 'Electronics', 'Average']` → selects
only the required columns in the specified order.
- `len(VisComm)` → displays the number of rows in the resulting
VisComm DataFrame.

Outcome:
- The Average column was calculated from the four recorded
subject scores.
- The VisComm DataFrame contains only students from
Visayas under the Communication track.
- The resulting VisComm DataFrame
contains 5 rows.
- Only the required columns Name, Gender, Math,
Electronics, and Average were retained.

---
