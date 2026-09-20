#  Data Wrangling and Data Visualization
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

### Code
```python
VisComm = board[(board["Hometown"] == "Visayas") & (board["Track"] == "Communication")]
[["Name", "Gender", "Math", "Electronics", "Average"]] #Creates a variable that contains the required columns
display(VisComm) #Displays the variable 'VisComm'
display(VisComm.shape[0]) #Displays the number of rows
```
### Output
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

### Code
```python
VisFemale = board[(board['Hometown'] == 'Visayas') & (board['Gender'] == 'Female')]
[['Name', 'Track', 'GEAS', 'Electronics', 'Average']] #Creates a variable that locates the hometown and gender
display(VisFemale) #Displays the variable 'VisFemale'
display(VisFemale.loc[VisFemale['Average']>60]) #Uses to locate the average that is greater than 60 and display
```

### Output
<img width="701" height="472" alt="image" src="https://github.com/user-attachments/assets/8e397dbf-9ef3-46a4-8fcf-f8aef413c4c4" />

### Explanation
The program calls the DataFrame containing the board values. It undergoes a filtering process where only the selected values for 'Hometown' and 'Gender' are kept, then stores the new data in a variable named 'VisFemale'. There are two displays in this program: the first display shows the new DataFrame stored in 'VisFemale', while the second locates rows with an average greater than 60 and displays those values.

## Changes
1. Added Description and Learning Outcome (09/20/2026)
2. Added the Information and Explanation for Problems 1 and 2 (09/20/2026)
