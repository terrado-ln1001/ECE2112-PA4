# Data Wrangling and Data Visualization
#### Terrado, Luke Nelson R.
#### 2ECE-A
------------------------
## Description
Data Wrangling and Data Visualization. Data Wrangling helps turn messy, raw information into clean, usable data for analysis. Data Visualization then presents this information as graphical elements, such as charts, graphs, and maps.

## Intended Learning Outcome
At the end of this laboratory activity, the student should be able to:
1. filter tabular data using several categorical and numerical conditions;
2. construct focused DataFrames by selecting relevant features;
3. summarize the relationship between categorical features and a numerical variable; and
4. communicate a data comparison using clear and correctly labeled plots.

---------------------------
## Download and Import
In Python, to import the Pandas library, simply use ```import pandas as pd```. Using the given CSV file called 'cars.csv', download the file and make sure that it is in the same location as the Jupyter notebook. To read the provided CSV file, enter ```pd.read_csv('board2.csv')``` inserted in a variable named 'board'.

-------------------------------
## 1. Visayas Communication DataFrame
Create a DataFrame named VisComm containing students whose Hometown is Visayas and whose Track is Communication. Retain only these columns, in the stated order:
- Name, Gender, Math, Electronics, Average

Display the resulting DataFrame and its number of rows. Both filtering conditions must be applied to the source dataset before the columns are selected

### ⚡ Code
```python
VisComm = board[(board["Hometown"] == "Visayas") & (board["Track"] == "Communication")]
[["Name", "Gender", "Math", "Electronics", "Average"]] #Creates a variable that contains the required columns
display(VisComm) #Displays the variable 'VisComm'
display(VisComm.shape[0]) #Displays the number of rows
```
### 🖨️ Output
<img width="403" height="262" alt="image" src="https://github.com/user-attachments/assets/27642780-0687-4f71-8433-5b5967d134ea" />

### Explanation
The program extracts data from the selected column and compares it until it matches the value being searched for. It then lists only the required column and stores it in the variable 'VisComm'. Finally, it displays the variable 'VisComm' and also displays the number of rows it collected.

--------------------------------
## 2. Visayas Female DataFrame
Create a second DataFrame named VisFemale containing students whose Hometown is Visayas and
whose Gender is Female. Retain only:
- Name, Track, GEAS, Electronics, Average

Display VisFemale. Then display only the rows of VisFemale whose Average is at least 60. Do not
overwrite VisFemale when performing this second filter.

### ⚡ Code
```python
VisFemale = board[(board['Hometown'] == 'Visayas') & (board['Gender'] == 'Female')]
[['Name', 'Track', 'GEAS', 'Electronics', 'Average']] #Creates a variable that locates the hometown and gender
display(VisFemale) #Displays the variable 'VisFemale'
display(VisFemale.loc[VisFemale['Average']>60]) #Uses to locate the average that is greater than 60 and display
```

### 🖨️ Output
<img width="701" height="472" alt="image" src="https://github.com/user-attachments/assets/8e397dbf-9ef3-46a4-8fcf-f8aef413c4c4" />

### Explanation
The program calls the DataFrame containing the board values. It undergoes a filtering process where only the selected values for 'Hometown' and 'Gender' are kept, then stores the new data in a variable named 'VisFemale'. There are two displays in this program: the first display shows the new DataFrame stored in 'VisFemale', while the second locates rows with an average greater than 60 and displays those values.

-------------------------
## 3. Category-Average Visualization
### 3.A) Mean of Average for every category
For each feature, compute the mean of Average for every category using Pandas.
### 3.B) Display
Display the three summary tables.

### ⚡ Code
```python
import pandas as pd
import matplotlib.pyplot as plt

# Mean Average by Track
track_summary = board.groupby('Track')['Average'].mean().reset_index()
print("Mean Average by Track:")
display(track_summary)

# Mean Average by Gender
gender_summary = board.groupby('Gender')['Average'].mean().reset_index()
print("\nMean Average by Gender:")
display(gender_summary)

# Mean Average by Hometown
hometown_summary = board.groupby('Hometown')['Average'].mean().reset_index()
print("\nMean Average by Hometown:")
display(hometown_summary)
```

### 🖨️ Output
<img width="243" height="564" alt="image" src="https://github.com/user-attachments/assets/55ab0626-3106-4d52-8c2b-32452654e065" />

### Explanation
This code imports Pandas and Matplotlib, then groups the dataset by three distinct categories—**Track**, **Gender**, and **Hometown**. It then calculates the mean score of the Average column for each group. For each summary, **.reset_index()** formats the grouped series back into a clean DataFrame structure. Finally, **display()** renders each resulting table alongside descriptive text printed before it.

### 3.C) Three Bar Charts
Create one figure containing three bar charts: mean Average by Track, by Gender, and by
Hometown.

### ⚡ Code
```python
#Creates one figure containing 3 subplots side-by-side
fig, axes = plt.subplots(1, 3, figsize=(16, 5), sharey=True)

# 1. Bar Chart by Track
axes[0].bar(track_summary['Track'], track_summary['Average'], color='skyblue', edgecolor='black')
axes[0].set_title('Mean Average by Track')
axes[0].set_xlabel('Track')
axes[0].set_ylabel('Mean Average Score')
axes[0].tick_params(axis='x', rotation=20)

# 2. Bar Chart by Gender
axes[1].bar(gender_summary['Gender'], gender_summary['Average'], color='salmon', edgecolor='black')
axes[1].set_title('Mean Average by Gender')
axes[1].set_xlabel('Gender')

# 3. Bar Chart by Hometown
axes[2].bar(hometown_summary['Hometown'], hometown_summary['Average'], color='lightgreen', edgecolor='black')
axes[2].set_title('Mean Average by Hometown')
axes[2].set_xlabel('Hometown')

plt.tight_layout()
plt.show()
```

### 🖨️ Output
<img width="1364" height="410" alt="image" src="https://github.com/user-attachments/assets/40adec93-6868-4755-8200-4e79a5a4d325" />

### Explanation
This code creates three subplots that are combined in one figure. It first creates the layout  **plt.subplot()** comparing average scores by track, gender, and hometown. Setting **sharey=True** ensures all three charts share the same Y-axis scale for easy visual comparison, while **figsize=(16, 5)** sets a wide aspect ratio. It enforces a consistent vertical scale across all charts for easy comparison, applies distinct colors and labels to each subplot, and automatically adjusts layout spacing before rendering the final visualization.

### 3.D) Three Concise Statements
Below the figure, write three concise statements identifying the category with the highest sample
mean for each feature.

### ⚡ Code
```python
top_track = track_summary.loc[track_summary['Average'].idxmax()]
top_gender = gender_summary.loc[gender_summary['Average'].idxmax()]
top_hometown = hometown_summary.loc[hometown_summary['Average'].idxmax()]

print(f"1. Track: The category with the highest sample mean is {top_track['Track']} ({top_track['Average']:.2f}).")
print(f"2. Gender: The category with the highest sample mean is {top_gender['Gender']} ({top_gender['Average']:.2f}).")
print(f"3. Hometown: The category with the highest sample mean is {top_hometown['Hometown']} ({top_hometown['Average']:.2f}).")
```

### 🖨️ Output
<img width="723" height="68" alt="image" src="https://github.com/user-attachments/assets/99f0b2da-c077-4ef9-97eb-462409573e92" />

### Explanation
The code creates three different variables that contain their corresponding summary of the information. It locates the average from each summary, then returns the index where the maximum value occurs. Finally, it prints formatted statements summarizing the top categories along with their corresponding maximum average scores rounded to two decimal places.

---------------------------------
## Changes
1. Added Description and Learning Outcome (09/20/2026)
2. Added the Information and Explanation for Problems 1 and 2 (09/20/2026)
3. Completed the missing information for Problem 3 (09/20/2026)
4. Uploaded the Jupyter File and CSV file (09/20/2026)
