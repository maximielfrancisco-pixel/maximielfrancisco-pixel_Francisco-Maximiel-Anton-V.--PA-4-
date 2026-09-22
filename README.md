# maximielfrancisco-pixel_Francisco-Maximiel-Anton-V.--PA-4-
---

### 1) A. Visayas Communication DataFrame - Filters students from Visayas under the Communication track and selects the required columns.

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

### 2) B. Visayas Female DataFrame - Filters female students from Visayas and then identifies those with an Average of at least 60.

```python
# Filter students whose Hometown is Visayas and whose Gender is Female
VisFemale = ECE.loc[
    (ECE['Hometown'] == 'Visayas')& 
    (ECE['Gender'] == 'Female'),
    ['Name', 'Track', 'GEAS', 'Electronics', 'Average']]

VisFemale3
# Display only VisFemale rows whose Average is at least 60
VisFemale.loc[VisFemale['Average'] >= 60]
VisComm
```
##### Step-by-Step Procedure of Functions:
- `ECE.loc[...]` → selects the required rows and columns from the
original ECE DataFrame.
- `(ECE['Hometown'] == 'Visayas')` → filters the dataset to students
whose Hometown is Visayas.
- `(ECE['Gender'] == 'Female')` → filters the dataset to female
students.
- `&` → combines both conditions so that a student must satisfy both
conditions.
- `['Name', 'Track', 'GEAS', 'Electronics', 'Average']` → selects only
the required columns.
- `VisFemale` → stores and displays the resulting Visayas Female
DataFrame.
- `VisFemale.loc[VisFemale['Average'] >= 60]` → displays only the rows
whose Average is at least 60 without changing the original VisFemale
DataFrame.

Outcome:
- The VisFemale DataFrame contains female students whose
Hometown is Visayas.
- The required columns Name, Track, GEAS,
Electronics, and Average were retained.
- The VisFemale DataFrame contains 6 rows.
- 4 of the VisFemale students have an Average of at
least 60. - The second filter does not overwrite VisFemale.

---

### 3) C. Category-Average Visualization - Computes the mean Average for Track, Gender, and Hometown and compares the results using bar charts.

```python
# Compute the mean Average for each Track
taverage = ECE.groupby('Track')['Average'].mean()
taverage

# Compute the mean Average for each Gender
gaverage = ECE.groupby('Gender')['Average'].mean()
gaverage

# Compute the mean Average for each Hometown
haverage = ECE.groupby('Hometown')['Average'].mean()
haverage

# Create one figure containing three bar charts
plt.figure(figsize=(12, 4))

# Average Comparison by Track
plt.subplot(1, 3, 1)
plt.bar(taverage.index, taverage.values)
plt.title('Average Comparison (Track)')
plt.xlabel('Track')
plt.ylabel('Average Grade')
plt.xticks(rotation=30)

# Average Comparison by Gender
plt.subplot(1, 3, 2)
plt.bar(gaverage.index, gaverage.values)
plt.title('Average Comparison (Gender)')
plt.xlabel('Gender')
plt.ylabel('Average Grade')

# Average Comparison by Hometown
plt.subplot(1, 3, 3)
plt.bar(haverage.index, haverage.values)
plt.title('Average Comparison (Hometown)')
plt.xlabel('Hometown')
plt.ylabel('Average Grade')
plt.xticks(rotation=30)

plt.tight_layout()
plt.show()
```
##### Step-by-Step Procedure of Functions:
- `ECE.groupby('Track')['Average'].mean()` → groups the students
according to Track and calculates the mean Average for each track.
- `ECE.groupby('Gender')['Average'].mean()` → groups the students
according to Gender and calculates the mean Average for each gender.
- `ECE.groupby('Hometown')['Average'].mean()` → groups the students
according to Hometown and calculates the mean Average for each
hometown.
- `taverage`, `gaverage`, and `haverage` → store the three
category-mean summaries.
- `plt.figure(figsize=(12, 4))` → creates one figure with enough space
for the three bar charts.
- `plt.subplot(1, 3, 1)` → creates the first plotting area for Track.
- `plt.subplot(1, 3, 2)` → creates the second plotting area for
Gender.
- `plt.subplot(1, 3, 3)` → creates the third plotting area for
Hometown.
- `plt.bar(...)` → creates a bar chart using the category names and
their corresponding mean Average values.
- `plt.title(...)` → gives each graph a descriptive title.
- `plt.xlabel(...)` → labels the horizontal axis.
- `plt.ylabel(...)` → labels the vertical axis as Average Grade.
- `plt.xticks(rotation=30) → rotates longer category labels to make
them easier to read.
- `plt.tight_layout()` → adjusts the spacing between the three charts.
plt.show() → displays the completed figure.

Outcome:
- Three summary tables were created for Track, Gender, and Hometown.
- The mean Average by Track was: Communication 67.975,Instrumentation 65.225, and Microelectronics 67.500.
- The mean Average by Gender was: Female 66.617 and Male 67.183.
- The mean Average by Hometown was Luzon 68.083, Mindanao 66.679, and Visayas 65.750.
- The three comparisons were displayed together in one figure using bar charts.

---

###  Interpretation of Category Means - Identifies the category with the highest sample mean for each categorical feature.

```python
# Identify the category with the highest sample mean for each feature
highest_track = taverage.idxmax()
highest_gender = gaverage.idxmax()
highest_hometown = haverage.idxmax()

print(f"Track: {highest_track} has the highest sample mean Average of {taverage.max():.2f}.")
print(f"Gender: {highest_gender} has the highest sample mean Average of {gaverage.max():.2f}.")
print(f"Hometown: {highest_hometown} has the highest sample mean Average of {haverage.max():.2f}.")
```
##### Step-by-Step Procedure of Functions:
- `taverage.idxmax()` → finds the Track category with the highest mean
Average.
- `gaverage.idxmax()` → finds the Gender category with the highest
mean Average.
- `haverage.idxmax()` → finds the Hometown category with the highest
mean Average.
- `taverage.max()` → gets the highest mean Average among the Track
categories.
- `gaverage.max()` → gets the highest mean Average among the Gender
categories.
- `haverage.max()` → gets the highest mean Average among the Hometown
categories.
- `:.2f` → formats each mean value to two decimal places.
- `print(...)` → displays the three interpretation statements.

 Outcome:
- Communication has the highest sample mean Average among the
Track categories at 67.98.
 - Male has the highest sample mean
Average among the Gender categories at 67.18.
 - Luzon has the
highest sample mean Average among the Hometown categories at 68.08.
 - These results describe differences observed in this dataset only; they
do not establish that Track, Gender, or Hometown causes a higher
board-exam score.
