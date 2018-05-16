

```python
import pandas as pd
import numpy as np

```

# Cleaning up the data and merging



```python
file1_csv = "students_complete.csv"
file2_csv = "schools_complete.csv"
```


```python
students_df = pd.read_csv(file1_csv)
schools_df = pd.read_csv(file2_csv)
```


```python
students_df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Unnamed: 0</th>
      <th>name</th>
      <th>gender</th>
      <th>grade</th>
      <th>school</th>
      <th>reading_score</th>
      <th>math_score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Paul Bradley</td>
      <td>M</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>66</td>
      <td>79</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Victor Smith</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>94</td>
      <td>61</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Kevin Rodriguez</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>90</td>
      <td>60</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Dr. Richard Scott</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>67</td>
      <td>58</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Bonnie Ray</td>
      <td>F</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>97</td>
      <td>84</td>
    </tr>
  </tbody>
</table>
</div>




```python
schools_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School ID</th>
      <th>name</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Figueroa High School</td>
      <td>District</td>
      <td>2949</td>
      <td>1884411</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Shelton High School</td>
      <td>Charter</td>
      <td>1761</td>
      <td>1056600</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Hernandez High School</td>
      <td>District</td>
      <td>4635</td>
      <td>3022020</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Griffin High School</td>
      <td>Charter</td>
      <td>1468</td>
      <td>917500</td>
    </tr>
    <tr>
      <th>5</th>
      <td>5</td>
      <td>Wilson High School</td>
      <td>Charter</td>
      <td>2283</td>
      <td>1319574</td>
    </tr>
    <tr>
      <th>6</th>
      <td>6</td>
      <td>Cabrera High School</td>
      <td>Charter</td>
      <td>1858</td>
      <td>1081356</td>
    </tr>
    <tr>
      <th>7</th>
      <td>7</td>
      <td>Bailey High School</td>
      <td>District</td>
      <td>4976</td>
      <td>3124928</td>
    </tr>
    <tr>
      <th>8</th>
      <td>8</td>
      <td>Holden High School</td>
      <td>Charter</td>
      <td>427</td>
      <td>248087</td>
    </tr>
    <tr>
      <th>9</th>
      <td>9</td>
      <td>Pena High School</td>
      <td>Charter</td>
      <td>962</td>
      <td>585858</td>
    </tr>
    <tr>
      <th>10</th>
      <td>10</td>
      <td>Wright High School</td>
      <td>Charter</td>
      <td>1800</td>
      <td>1049400</td>
    </tr>
    <tr>
      <th>11</th>
      <td>11</td>
      <td>Rodriguez High School</td>
      <td>District</td>
      <td>3999</td>
      <td>2547363</td>
    </tr>
    <tr>
      <th>12</th>
      <td>12</td>
      <td>Johnson High School</td>
      <td>District</td>
      <td>4761</td>
      <td>3094650</td>
    </tr>
    <tr>
      <th>13</th>
      <td>13</td>
      <td>Ford High School</td>
      <td>District</td>
      <td>2739</td>
      <td>1763916</td>
    </tr>
    <tr>
      <th>14</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
    </tr>
  </tbody>
</table>
</div>




```python
schools_df.columns

```




    Index(['School ID', 'name', 'type', 'size', 'budget'], dtype='object')




```python
schools_df = schools_df.rename(columns={"name":"school"})
```


```python
merge_df = pd.merge(students_df,schools_df, on='school')
```


```python
merge_df.max()
```




    Unnamed: 0                    39169
    name                      Zoe Meyer
    gender                            M
    grade                           9th
    school           Wright High School
    reading_score                    99
    math_score                       99
    School ID                        14
    type                       District
    size                           4976
    budget                      3124928
    dtype: object




```python
#duplicated score rows to clean up for later calculations
merge_df['Math_Info'] = merge_df['math_score']
merge_df['Reading_Info']=merge_df['reading_score']
#merge_df["grade"] = pd.to_numeric(merge_df["grade"])
merge_df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Unnamed: 0</th>
      <th>name</th>
      <th>gender</th>
      <th>grade</th>
      <th>school</th>
      <th>reading_score</th>
      <th>math_score</th>
      <th>School ID</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
      <th>Math_Info</th>
      <th>Reading_Info</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Paul Bradley</td>
      <td>M</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>66</td>
      <td>79</td>
      <td>0</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>79</td>
      <td>66</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Victor Smith</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>94</td>
      <td>61</td>
      <td>0</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>61</td>
      <td>94</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Kevin Rodriguez</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>90</td>
      <td>60</td>
      <td>0</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>60</td>
      <td>90</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Dr. Richard Scott</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>67</td>
      <td>58</td>
      <td>0</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>58</td>
      <td>67</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Bonnie Ray</td>
      <td>F</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>97</td>
      <td>84</td>
      <td>0</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>84</td>
      <td>97</td>
    </tr>
  </tbody>
</table>
</div>




```python
#School_Passing_Math clean up data work

bins = [0, 69, 100]

# Create the names for the bins
group_names = [0, 1]
Math_Passing_Tally = pd.cut(merge_df["math_score"], bins, labels=group_names)

merge_df["Math_Info"] = Math_Passing_Tally


merge_df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Unnamed: 0</th>
      <th>name</th>
      <th>gender</th>
      <th>grade</th>
      <th>school</th>
      <th>reading_score</th>
      <th>math_score</th>
      <th>School ID</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
      <th>Math_Info</th>
      <th>Reading_Info</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Paul Bradley</td>
      <td>M</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>66</td>
      <td>79</td>
      <td>0</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>1</td>
      <td>66</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Victor Smith</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>94</td>
      <td>61</td>
      <td>0</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>0</td>
      <td>94</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Kevin Rodriguez</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>90</td>
      <td>60</td>
      <td>0</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>0</td>
      <td>90</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Dr. Richard Scott</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>67</td>
      <td>58</td>
      <td>0</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>0</td>
      <td>67</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Bonnie Ray</td>
      <td>F</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>97</td>
      <td>84</td>
      <td>0</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>1</td>
      <td>97</td>
    </tr>
  </tbody>
</table>
</div>




```python
#Clean up data for reading score calculations
bins = [0, 69, 100]

# Create the names bins with values- 
group_names = [0, 1]
Reading_Passing_Tally = pd.cut(merge_df["reading_score"], bins, labels=group_names)

merge_df["Reading_Info"] = Reading_Passing_Tally
merge_df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Unnamed: 0</th>
      <th>name</th>
      <th>gender</th>
      <th>grade</th>
      <th>school</th>
      <th>reading_score</th>
      <th>math_score</th>
      <th>School ID</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
      <th>Math_Info</th>
      <th>Reading_Info</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Paul Bradley</td>
      <td>M</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>66</td>
      <td>79</td>
      <td>0</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Victor Smith</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>94</td>
      <td>61</td>
      <td>0</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Kevin Rodriguez</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>90</td>
      <td>60</td>
      <td>0</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Dr. Richard Scott</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>67</td>
      <td>58</td>
      <td>0</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Bonnie Ray</td>
      <td>F</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>97</td>
      <td>84</td>
      <td>0</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>1</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>




```python
merge_df["Math_Info"] = pd.to_numeric(merge_df["Math_Info"])
merge_df["Reading_Info"]= pd.to_numeric(merge_df["Reading_Info"])
```

# Code for "District Summary" results


```python
total_students = students_df['name'].count()

total_schools = schools_df['school'].count()

total_budget = schools_df['budget'].sum()

Average_district_Math = round(merge_df['math_score'].mean(),1)

average_district_reading = round(merge_df['reading_score'].mean(),1)

district_passing_math = merge_df.loc[(merge_df['math_score']>69)]

average_passing_math = round(district_passing_math['name'].count()/total_students*100,1)

district_passing_reading = merge_df.loc[(merge_df['reading_score']>69)]

average_passing_reading = round(district_passing_reading['name'].count()/total_students*100,1)

over_all_passing_rate = (average_passing_math+average_passing_reading)/2


```


```python
District_Summary_df = pd.DataFrame({"Total Schools" :[total_schools],"Total Students":[total_students],
                                    "Total Budget":[total_budget],"Average Math Score":[Average_district_Math],
                                   "Average Reading Score":[average_district_reading],
                                    "% Passing Math":[average_passing_math],
                                    "% Passing Reading":[average_passing_reading],
                                   "Overall Passing Rate":[over_all_passing_rate]})

District_Summary_df["Total Budget"] = District_Summary_df["Total Budget"].map("${:,.2f}".format)
District_Summary_df["% Passing Math"] = District_Summary_df["% Passing Math"].map("{:,.1f}%".format)
District_Summary_df["% Passing Reading"] = District_Summary_df["% Passing Reading"].map("{:,.1f}%".format)
District_Summary_df["Overall Passing Rate"] = District_Summary_df["Overall Passing Rate"].map("{:,.1f}%".format)

Final_District_summary = District_Summary_df[["Total Schools","Total Students","Total Budget", "Average Math Score",
                                             "Average Reading Score","% Passing Math","% Passing Reading",
                                              "Overall Passing Rate"]]
```

# District Summary



```python
Final_District_summary

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Total Schools</th>
      <th>Total Students</th>
      <th>Total Budget</th>
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>Overall Passing Rate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>15</td>
      <td>39170</td>
      <td>$24,649,428.00</td>
      <td>79.0</td>
      <td>81.9</td>
      <td>75.0%</td>
      <td>85.8%</td>
      <td>80.4%</td>
    </tr>
  </tbody>
</table>
</div>



#   Code/Work for the "School Summary"


```python
School_Summary = merge_df[['school', 'type','name', 'gender', 'grade', 'reading_score',
       'math_score', 'School ID', 'size', 'budget','Math_Info','Reading_Info']]

School_Summary.head()

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>school</th>
      <th>type</th>
      <th>name</th>
      <th>gender</th>
      <th>grade</th>
      <th>reading_score</th>
      <th>math_score</th>
      <th>School ID</th>
      <th>size</th>
      <th>budget</th>
      <th>Math_Info</th>
      <th>Reading_Info</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Huang High School</td>
      <td>District</td>
      <td>Paul Bradley</td>
      <td>M</td>
      <td>9th</td>
      <td>66</td>
      <td>79</td>
      <td>0</td>
      <td>2917</td>
      <td>1910635</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Huang High School</td>
      <td>District</td>
      <td>Victor Smith</td>
      <td>M</td>
      <td>12th</td>
      <td>94</td>
      <td>61</td>
      <td>0</td>
      <td>2917</td>
      <td>1910635</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Huang High School</td>
      <td>District</td>
      <td>Kevin Rodriguez</td>
      <td>M</td>
      <td>12th</td>
      <td>90</td>
      <td>60</td>
      <td>0</td>
      <td>2917</td>
      <td>1910635</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Huang High School</td>
      <td>District</td>
      <td>Dr. Richard Scott</td>
      <td>M</td>
      <td>12th</td>
      <td>67</td>
      <td>58</td>
      <td>0</td>
      <td>2917</td>
      <td>1910635</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Huang High School</td>
      <td>District</td>
      <td>Bonnie Ray</td>
      <td>F</td>
      <td>9th</td>
      <td>97</td>
      <td>84</td>
      <td>0</td>
      <td>2917</td>
      <td>1910635</td>
      <td>1</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>




```python
#confirmed the math_info and reading_info as int64
merge_df.dtypes
```




    Unnamed: 0        int64
    name             object
    gender           object
    grade            object
    school           object
    reading_score     int64
    math_score        int64
    School ID         int64
    type             object
    size              int64
    budget            int64
    Math_Info         int64
    Reading_Info      int64
    dtype: object




```python
school_groups = School_Summary.groupby("school")
school_groups.max()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>type</th>
      <th>name</th>
      <th>gender</th>
      <th>grade</th>
      <th>reading_score</th>
      <th>math_score</th>
      <th>School ID</th>
      <th>size</th>
      <th>budget</th>
      <th>Math_Info</th>
      <th>Reading_Info</th>
    </tr>
    <tr>
      <th>school</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Bailey High School</th>
      <td>District</td>
      <td>Zachary Williams</td>
      <td>M</td>
      <td>9th</td>
      <td>99</td>
      <td>99</td>
      <td>7</td>
      <td>4976</td>
      <td>3124928</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>Charter</td>
      <td>Zoe Gaines</td>
      <td>M</td>
      <td>9th</td>
      <td>99</td>
      <td>99</td>
      <td>6</td>
      <td>1858</td>
      <td>1081356</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>District</td>
      <td>Zachary Wyatt</td>
      <td>M</td>
      <td>9th</td>
      <td>99</td>
      <td>99</td>
      <td>1</td>
      <td>2949</td>
      <td>1884411</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>District</td>
      <td>Zoe Burton</td>
      <td>M</td>
      <td>9th</td>
      <td>99</td>
      <td>99</td>
      <td>13</td>
      <td>2739</td>
      <td>1763916</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>Charter</td>
      <td>Zoe Burgess</td>
      <td>M</td>
      <td>9th</td>
      <td>99</td>
      <td>99</td>
      <td>4</td>
      <td>1468</td>
      <td>917500</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>District</td>
      <td>Zoe Meyer</td>
      <td>M</td>
      <td>9th</td>
      <td>99</td>
      <td>99</td>
      <td>3</td>
      <td>4635</td>
      <td>3022020</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>Charter</td>
      <td>Zoe Hawkins</td>
      <td>M</td>
      <td>9th</td>
      <td>99</td>
      <td>99</td>
      <td>8</td>
      <td>427</td>
      <td>248087</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>District</td>
      <td>Zoe Mcmillan</td>
      <td>M</td>
      <td>9th</td>
      <td>99</td>
      <td>99</td>
      <td>0</td>
      <td>2917</td>
      <td>1910635</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>District</td>
      <td>Zachary Whitney</td>
      <td>M</td>
      <td>9th</td>
      <td>99</td>
      <td>99</td>
      <td>12</td>
      <td>4761</td>
      <td>3094650</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>Charter</td>
      <td>Zachary Pruitt</td>
      <td>M</td>
      <td>9th</td>
      <td>99</td>
      <td>99</td>
      <td>9</td>
      <td>962</td>
      <td>585858</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>District</td>
      <td>Zachary Winters</td>
      <td>M</td>
      <td>9th</td>
      <td>99</td>
      <td>99</td>
      <td>11</td>
      <td>3999</td>
      <td>2547363</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>Charter</td>
      <td>Zoe Mayer</td>
      <td>M</td>
      <td>9th</td>
      <td>99</td>
      <td>99</td>
      <td>2</td>
      <td>1761</td>
      <td>1056600</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>Charter</td>
      <td>Zoe Allen</td>
      <td>M</td>
      <td>9th</td>
      <td>99</td>
      <td>99</td>
      <td>14</td>
      <td>1635</td>
      <td>1043130</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>Charter</td>
      <td>Zoe Hawkins</td>
      <td>M</td>
      <td>9th</td>
      <td>99</td>
      <td>99</td>
      <td>5</td>
      <td>2283</td>
      <td>1319574</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>Charter</td>
      <td>Zachary Smith</td>
      <td>M</td>
      <td>9th</td>
      <td>99</td>
      <td>99</td>
      <td>10</td>
      <td>1800</td>
      <td>1049400</td>
      <td>1</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>




```python
school_student_counts = School_Summary["school"].value_counts()
school_types = school_groups['type'].max()
school_budget = school_groups['budget'].max()
School_per_student_Budget = school_budget/school_student_counts
#average Math score
students_average_math_score = school_groups['math_score'].mean()
mathcount = school_groups["Math_Info"].sum()
#Mathpassing = mathcount/school_student_counts.head()
readingcount = school_groups["Reading_Info"].sum()
#average reading score
students_average_reading_score = school_groups['reading_score'].mean()
#% passing Math
School_mathpassing_rate = round(mathcount/school_student_counts*100)
#% passing reading
School_readingpassing_rate = round(readingcount/school_student_counts*100)
#overall passing rate
school_overall_passing = round((School_mathpassing_rate+School_readingpassing_rate)/2)
```


```python
Complete_School_Data = pd.DataFrame({"Type": school_types,"Total Students": school_student_counts, 
                                 "Total School Budget": school_budget, "Per Student Budget":School_per_student_Budget,
                                 "Avgerage Math Score":students_average_math_score, 
                                 "Average Reading Score":students_average_reading_score,
                                  "% Passing Math":School_mathpassing_rate, "% Passing Reading":School_readingpassing_rate,
                                 "% Overall Passing Rate": school_overall_passing})




Final_School_Data = Complete_School_Data[["Type","Total Students","Total School Budget", "Per Student Budget",
                                 "Avgerage Math Score","Average Reading Score","% Passing Math", "% Passing Reading",
                                 "% Overall Passing Rate"]]
Final_School_Data["Per Student Budget"]=Final_School_Data["Per Student Budget"].map("${:,.2f}".format)
Final_School_Data["Total School Budget"]=Final_School_Data["Total School Budget"].map("${:,.2f}".format)
Final_School_Data["% Passing Math"]=Final_School_Data["% Passing Math"].map("{:,.1f}%".format)
Final_School_Data["% Passing Reading"]=Final_School_Data["% Passing Reading"].map("{:,.1f}%".format)
Final_School_Data["% Overall Passing Rate"]=Final_School_Data["% Overall Passing Rate"].map("{:,.1f}%".format)
```

# School Summary


```python
Final_School_Data
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Type</th>
      <th>Total Students</th>
      <th>Total School Budget</th>
      <th>Per Student Budget</th>
      <th>Avgerage Math Score</th>
      <th>Average Reading Score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>% Overall Passing Rate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Bailey High School</th>
      <td>District</td>
      <td>4976</td>
      <td>$3,124,928.00</td>
      <td>$628.00</td>
      <td>77.048432</td>
      <td>81.033963</td>
      <td>67.0%</td>
      <td>82.0%</td>
      <td>74.0%</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>Charter</td>
      <td>1858</td>
      <td>$1,081,356.00</td>
      <td>$582.00</td>
      <td>83.061895</td>
      <td>83.975780</td>
      <td>94.0%</td>
      <td>97.0%</td>
      <td>96.0%</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>District</td>
      <td>2949</td>
      <td>$1,884,411.00</td>
      <td>$639.00</td>
      <td>76.711767</td>
      <td>81.158020</td>
      <td>66.0%</td>
      <td>81.0%</td>
      <td>74.0%</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>District</td>
      <td>2739</td>
      <td>$1,763,916.00</td>
      <td>$644.00</td>
      <td>77.102592</td>
      <td>80.746258</td>
      <td>68.0%</td>
      <td>79.0%</td>
      <td>74.0%</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>Charter</td>
      <td>1468</td>
      <td>$917,500.00</td>
      <td>$625.00</td>
      <td>83.351499</td>
      <td>83.816757</td>
      <td>93.0%</td>
      <td>97.0%</td>
      <td>95.0%</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>District</td>
      <td>4635</td>
      <td>$3,022,020.00</td>
      <td>$652.00</td>
      <td>77.289752</td>
      <td>80.934412</td>
      <td>67.0%</td>
      <td>81.0%</td>
      <td>74.0%</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>Charter</td>
      <td>427</td>
      <td>$248,087.00</td>
      <td>$581.00</td>
      <td>83.803279</td>
      <td>83.814988</td>
      <td>93.0%</td>
      <td>96.0%</td>
      <td>94.0%</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>District</td>
      <td>2917</td>
      <td>$1,910,635.00</td>
      <td>$655.00</td>
      <td>76.629414</td>
      <td>81.182722</td>
      <td>66.0%</td>
      <td>81.0%</td>
      <td>74.0%</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>District</td>
      <td>4761</td>
      <td>$3,094,650.00</td>
      <td>$650.00</td>
      <td>77.072464</td>
      <td>80.966394</td>
      <td>66.0%</td>
      <td>81.0%</td>
      <td>74.0%</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>Charter</td>
      <td>962</td>
      <td>$585,858.00</td>
      <td>$609.00</td>
      <td>83.839917</td>
      <td>84.044699</td>
      <td>95.0%</td>
      <td>96.0%</td>
      <td>96.0%</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>District</td>
      <td>3999</td>
      <td>$2,547,363.00</td>
      <td>$637.00</td>
      <td>76.842711</td>
      <td>80.744686</td>
      <td>66.0%</td>
      <td>80.0%</td>
      <td>73.0%</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>Charter</td>
      <td>1761</td>
      <td>$1,056,600.00</td>
      <td>$600.00</td>
      <td>83.359455</td>
      <td>83.725724</td>
      <td>94.0%</td>
      <td>96.0%</td>
      <td>95.0%</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>Charter</td>
      <td>1635</td>
      <td>$1,043,130.00</td>
      <td>$638.00</td>
      <td>83.418349</td>
      <td>83.848930</td>
      <td>93.0%</td>
      <td>97.0%</td>
      <td>95.0%</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>Charter</td>
      <td>2283</td>
      <td>$1,319,574.00</td>
      <td>$578.00</td>
      <td>83.274201</td>
      <td>83.989488</td>
      <td>94.0%</td>
      <td>97.0%</td>
      <td>96.0%</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>Charter</td>
      <td>1800</td>
      <td>$1,049,400.00</td>
      <td>$583.00</td>
      <td>83.682222</td>
      <td>83.955000</td>
      <td>93.0%</td>
      <td>97.0%</td>
      <td>95.0%</td>
    </tr>
  </tbody>
</table>
</div>



# Greatest Performing School By Passing Rate



```python
Greatest_Performing = Final_School_Data.sort_values("% Overall Passing Rate", ascending=False)
Greatest_Performing.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Type</th>
      <th>Total Students</th>
      <th>Total School Budget</th>
      <th>Per Student Budget</th>
      <th>Avgerage Math Score</th>
      <th>Average Reading Score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>% Overall Passing Rate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Cabrera High School</th>
      <td>Charter</td>
      <td>1858</td>
      <td>$1,081,356.00</td>
      <td>$582.00</td>
      <td>83.061895</td>
      <td>83.975780</td>
      <td>94.0%</td>
      <td>97.0%</td>
      <td>96.0%</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>Charter</td>
      <td>962</td>
      <td>$585,858.00</td>
      <td>$609.00</td>
      <td>83.839917</td>
      <td>84.044699</td>
      <td>95.0%</td>
      <td>96.0%</td>
      <td>96.0%</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>Charter</td>
      <td>2283</td>
      <td>$1,319,574.00</td>
      <td>$578.00</td>
      <td>83.274201</td>
      <td>83.989488</td>
      <td>94.0%</td>
      <td>97.0%</td>
      <td>96.0%</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>Charter</td>
      <td>1468</td>
      <td>$917,500.00</td>
      <td>$625.00</td>
      <td>83.351499</td>
      <td>83.816757</td>
      <td>93.0%</td>
      <td>97.0%</td>
      <td>95.0%</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>Charter</td>
      <td>1761</td>
      <td>$1,056,600.00</td>
      <td>$600.00</td>
      <td>83.359455</td>
      <td>83.725724</td>
      <td>94.0%</td>
      <td>96.0%</td>
      <td>95.0%</td>
    </tr>
  </tbody>
</table>
</div>



# Lowest Performing School by Passing Rate



```python
Lowest_Performing = Final_School_Data.sort_values("% Overall Passing Rate", ascending=True)
Lowest_Performing.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Type</th>
      <th>Total Students</th>
      <th>Total School Budget</th>
      <th>Per Student Budget</th>
      <th>Avgerage Math Score</th>
      <th>Average Reading Score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>% Overall Passing Rate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Rodriguez High School</th>
      <td>District</td>
      <td>3999</td>
      <td>$2,547,363.00</td>
      <td>$637.00</td>
      <td>76.842711</td>
      <td>80.744686</td>
      <td>66.0%</td>
      <td>80.0%</td>
      <td>73.0%</td>
    </tr>
    <tr>
      <th>Bailey High School</th>
      <td>District</td>
      <td>4976</td>
      <td>$3,124,928.00</td>
      <td>$628.00</td>
      <td>77.048432</td>
      <td>81.033963</td>
      <td>67.0%</td>
      <td>82.0%</td>
      <td>74.0%</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>District</td>
      <td>2949</td>
      <td>$1,884,411.00</td>
      <td>$639.00</td>
      <td>76.711767</td>
      <td>81.158020</td>
      <td>66.0%</td>
      <td>81.0%</td>
      <td>74.0%</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>District</td>
      <td>2739</td>
      <td>$1,763,916.00</td>
      <td>$644.00</td>
      <td>77.102592</td>
      <td>80.746258</td>
      <td>68.0%</td>
      <td>79.0%</td>
      <td>74.0%</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>District</td>
      <td>4635</td>
      <td>$3,022,020.00</td>
      <td>$652.00</td>
      <td>77.289752</td>
      <td>80.934412</td>
      <td>67.0%</td>
      <td>81.0%</td>
      <td>74.0%</td>
    </tr>
  </tbody>
</table>
</div>



# Code/Work for "Math Score by Grade"


```python
School_Summary_For_Mathgrade = merge_df[['school','grade','math_score',]]

Grade9_Mathstuff = School_Summary_For_Mathgrade.loc[School_Summary_For_Mathgrade["grade"] == "9th", :]
Grade9_Mathstuff.head()
school_counts = Grade9_Mathstuff["school"].value_counts()
school_counts.head()
grouped_9th = Grade9_Mathstuff.groupby(['school'])
grouped_9th.mean().head()
Grade9_Mathcounts = grouped_9th["math_score"].mean()


```


```python
School_Summary_For_Mathgrade = merge_df[['school','grade','math_score',]]

Grade10_Mathstuff = School_Summary_For_Mathgrade.loc[School_Summary_For_Mathgrade["grade"] == "10th", :]
Grade10_Mathstuff.head()
school_10counts = Grade10_Mathstuff["school"].value_counts()
school_10counts.head()
grouped_10th = Grade10_Mathstuff.groupby(['school'])
grouped_10th.mean().head()
Grade10_Mathcounts = grouped_10th["math_score"].mean()


```


```python
School_Summary_For_Mathgrade = merge_df[['school','grade','math_score',]]

Grade11_Mathstuff = School_Summary_For_Mathgrade.loc[School_Summary_For_Mathgrade["grade"] == "11th", :]
Grade11_Mathstuff.head()
school_11counts = Grade11_Mathstuff["school"].value_counts()
school_11counts.head()
grouped_11th = Grade11_Mathstuff.groupby(['school'])
grouped_11th.mean().head()
Grade11_Mathcounts = grouped_11th["math_score"].mean()

```


```python
School_Summary_For_Mathgrade = merge_df[['school','grade','math_score',]]

Grade12_Mathstuff = School_Summary_For_Mathgrade.loc[School_Summary_For_Mathgrade["grade"] == "12th", :]
Grade12_Mathstuff.head()
school_12counts = Grade12_Mathstuff["school"].value_counts()
school_12counts.head()
grouped_12th = Grade10_Mathstuff.groupby(['school'])
grouped_12th.mean().head()
Grade12_Mathcounts = grouped_12th["math_score"].mean()

```

# Math Score by Grade



```python
All_GradesByMath_df = pd.DataFrame({"9th":Grade9_Mathcounts, "10th":Grade10_Mathcounts, "11th":Grade11_Mathcounts,
                                   "12th":Grade12_Mathcounts})
Final_All_GradesByMath_df = All_GradesByMath_df[["9th","10th","11th","12th"]]
Final_All_GradesByMath_df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>9th</th>
      <th>10th</th>
      <th>11th</th>
      <th>12th</th>
    </tr>
    <tr>
      <th>school</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Bailey High School</th>
      <td>77.083676</td>
      <td>76.996772</td>
      <td>77.515588</td>
      <td>76.996772</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>83.094697</td>
      <td>83.154506</td>
      <td>82.765560</td>
      <td>83.154506</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>76.403037</td>
      <td>76.539974</td>
      <td>76.884344</td>
      <td>76.539974</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>77.361345</td>
      <td>77.672316</td>
      <td>76.918058</td>
      <td>77.672316</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>82.044010</td>
      <td>84.229064</td>
      <td>83.842105</td>
      <td>84.229064</td>
    </tr>
  </tbody>
</table>
</div>



# Code/Work for "Reading Scores by Grade"


```python
School_Summary_For_Readinggrades = merge_df[['school','grade', 'reading_score',]]
ReadingGrades = School_Summary_For_Readinggrades.groupby("school")

Grade9_Readingstuff = School_Summary_For_Readinggrades.loc[School_Summary_For_Readinggrades["grade"] == "9th", :]
SchoolReading_9Counts = Grade9_Readingstuff["school"].value_counts()
groupedReading_9th = Grade9_Readingstuff.groupby(['school'])
groupedReading_9th.mean().head()
Grade9_Readcounts = groupedReading_9th["reading_score"].mean()


```


```python
School_Summary_For_Readinggrades = merge_df[['school','grade', 'reading_score',]]
ReadingGrades = School_Summary_For_Readinggrades.groupby("school")

Grade10_Readingstuff = School_Summary_For_Readinggrades.loc[School_Summary_For_Readinggrades["grade"] == "10th", :]
SchoolReading_10Counts = Grade10_Readingstuff["school"].value_counts()
groupedReading_10th = Grade10_Readingstuff.groupby(['school'])
groupedReading_10th.mean().head()
Grade10_Readcounts = groupedReading_10th["reading_score"].mean()
```


```python
School_Summary_For_Readinggrades = merge_df[['school','grade', 'reading_score',]]
ReadingGrades = School_Summary_For_Readinggrades.groupby("school")

Grade11_Readingstuff = School_Summary_For_Readinggrades.loc[School_Summary_For_Readinggrades["grade"] == "11th", :]
SchoolReading_11Counts = Grade11_Readingstuff["school"].value_counts()
groupedReading_11th = Grade11_Readingstuff.groupby(['school'])
groupedReading_11th.mean().head()
Grade11_Readcounts = groupedReading_11th["reading_score"].mean()
```


```python
School_Summary_For_Readinggrades = merge_df[['school','grade', 'reading_score',]]
ReadingGrades = School_Summary_For_Readinggrades.groupby("school")

Grade12_Readingstuff = School_Summary_For_Readinggrades.loc[School_Summary_For_Readinggrades["grade"] == "12th", :]
SchoolReading_12Counts = Grade12_Readingstuff["school"].value_counts()
groupedReading_12th = Grade12_Readingstuff.groupby(['school'])
groupedReading_12th.mean().head()
Grade12_Readcounts = groupedReading_12th["reading_score"].mean()
```

# Reading Scores by Grades


```python
All_GradesByReading_df = pd.DataFrame({"9th":Grade9_Readcounts, "10th":Grade10_Readcounts, 
                                       "11th":Grade11_Readcounts,"12th":Grade12_Readcounts})
Final_All_GradesByRead_df = All_GradesByReading_df[["9th","10th","11th","12th"]]
Final_All_GradesByRead_df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>9th</th>
      <th>10th</th>
      <th>11th</th>
      <th>12th</th>
    </tr>
    <tr>
      <th>school</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Bailey High School</th>
      <td>81.303155</td>
      <td>80.907183</td>
      <td>80.945643</td>
      <td>80.912451</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>83.676136</td>
      <td>84.253219</td>
      <td>83.788382</td>
      <td>84.287958</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>81.198598</td>
      <td>81.408912</td>
      <td>80.640339</td>
      <td>81.384863</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>80.632653</td>
      <td>81.262712</td>
      <td>80.403642</td>
      <td>80.662338</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>83.369193</td>
      <td>83.706897</td>
      <td>84.288089</td>
      <td>84.013699</td>
    </tr>
  </tbody>
</table>
</div>



# Code/Work for "Spending Ranges (Per Student)"


```python

#Final_School_Data.max() showed $655
#Final_School_Data.min() showed $578

Spending_Per_student_Data = Complete_School_Data[["Per Student Budget","Avgerage Math Score","Average Reading Score",
                                                  "% Passing Math", "% Passing Reading","% Overall Passing Rate"]]
bins_Spending_per_student = [0, 585, 615, 645, 675]

group_Spending = ['<\$585', '\$585 - $615', '\$615 - $645', '\$645 - $675']
Per_student_Spending_series = pd.cut(Spending_Per_student_Data["Per Student Budget"], bins_Spending_per_student,
                                     labels=group_Spending)
Spending_Per_student_Data["Per Student Budget"]=Spending_Per_student_Data["Per Student Budget"].map("${:,.2f}".format)
Spending_Per_student_Data["Spending Ranges(Per Student)"] = Per_student_Spending_series

Spending_Per_student_Ranges = Spending_Per_student_Data.groupby("Spending Ranges(Per Student)")


```

    /anaconda3/lib/python3.6/site-packages/ipykernel_launcher.py:12: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: http://pandas.pydata.org/pandas-docs/stable/indexing.html#indexing-view-versus-copy
      if sys.path[0] == '':
    /anaconda3/lib/python3.6/site-packages/ipykernel_launcher.py:13: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: http://pandas.pydata.org/pandas-docs/stable/indexing.html#indexing-view-versus-copy
      del sys.path[0]


# Spending Ranges (per student)


```python
Spending_Per_student_Ranges.mean()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Avgerage Math Score</th>
      <th>Average Reading Score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>% Overall Passing Rate</th>
    </tr>
    <tr>
      <th>Spending Ranges(Per Student)</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>&lt;\$585</th>
      <td>83.455399</td>
      <td>83.933814</td>
      <td>93.500000</td>
      <td>96.75</td>
      <td>95.250000</td>
    </tr>
    <tr>
      <th>\$585 - $615</th>
      <td>83.599686</td>
      <td>83.885211</td>
      <td>94.500000</td>
      <td>96.00</td>
      <td>95.500000</td>
    </tr>
    <tr>
      <th>\$615 - $645</th>
      <td>79.079225</td>
      <td>81.891436</td>
      <td>75.500000</td>
      <td>86.00</td>
      <td>80.833333</td>
    </tr>
    <tr>
      <th>\$645 - $675</th>
      <td>76.997210</td>
      <td>81.027843</td>
      <td>66.333333</td>
      <td>81.00</td>
      <td>74.000000</td>
    </tr>
  </tbody>
</table>
</div>



# Code/Work for "Scores by School Size"


```python
#Scores by School size
#Total Students Max = 4976
#Total Students Min = 427

School_Size_Data = Complete_School_Data[["Total Students","Avgerage Math Score","Average Reading Score",
                                                  "% Passing Math", "% Passing Reading","% Overall Passing Rate"]]

bins_school_size = [0, 1000, 2000, 5000]

group_Size = ['Small <1000', 'Medium 1000-2000', 'Large 2000-5000']
School_Size_series = pd.cut(School_Size_Data["Total Students"], bins_school_size,
                                     labels=group_Size)
School_Size_Data["Total Students"]=School_Size_Data["Total Students"].map("${:,.2f}".format)
School_Size_Data["Scores By School Size"] = School_Size_series

School_Size_Ranges = School_Size_Data.groupby("Scores By School Size")

```

    /anaconda3/lib/python3.6/site-packages/ipykernel_launcher.py:13: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: http://pandas.pydata.org/pandas-docs/stable/indexing.html#indexing-view-versus-copy
      del sys.path[0]
    /anaconda3/lib/python3.6/site-packages/ipykernel_launcher.py:14: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: http://pandas.pydata.org/pandas-docs/stable/indexing.html#indexing-view-versus-copy
      


# Scores by School Size


```python
School_Size_Ranges.mean()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Avgerage Math Score</th>
      <th>Average Reading Score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>% Overall Passing Rate</th>
    </tr>
    <tr>
      <th>Scores By School Size</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Small &lt;1000</th>
      <td>83.821598</td>
      <td>83.929843</td>
      <td>94.0</td>
      <td>96.00</td>
      <td>95.000</td>
    </tr>
    <tr>
      <th>Medium 1000-2000</th>
      <td>83.374684</td>
      <td>83.864438</td>
      <td>93.4</td>
      <td>96.80</td>
      <td>95.200</td>
    </tr>
    <tr>
      <th>Large 2000-5000</th>
      <td>77.746417</td>
      <td>81.344493</td>
      <td>70.0</td>
      <td>82.75</td>
      <td>76.625</td>
    </tr>
  </tbody>
</table>
</div>



# Grades by School Type


```python
#Group Data by Type of school
Type_School_Data = Complete_School_Data[["Type","Avgerage Math Score","Average Reading Score","% Passing Math", 
                                         "% Passing Reading",
                                 "% Overall Passing Rate"]]
Type_Schools = Type_School_Data.groupby("Type")
Type_Schools.max()


```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Avgerage Math Score</th>
      <th>Average Reading Score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>% Overall Passing Rate</th>
    </tr>
    <tr>
      <th>Type</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Charter</th>
      <td>83.839917</td>
      <td>84.044699</td>
      <td>95.0</td>
      <td>97.0</td>
      <td>96.0</td>
    </tr>
    <tr>
      <th>District</th>
      <td>77.289752</td>
      <td>81.182722</td>
      <td>68.0</td>
      <td>82.0</td>
      <td>74.0</td>
    </tr>
  </tbody>
</table>
</div>


