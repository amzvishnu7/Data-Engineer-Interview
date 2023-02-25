## Tiger Analytics - Skill Test Questions

### Section - 1 - SCALA / Python ( All Codes Below Given are Python Codes )

#### Q1. Have a list of 3 letters. Write a Python/Scala code to concatenate this list with another list of numbers whose range varies from 1 to 3 (3 is included).
letters list = ['A', 'B', 'C]

**Expected Output:** [A1', 'B1', 'C1', 'A2', 'B2', 'C2', 'A3', 'B3', 'C3']

```python
letters = ['A', 'B', 'C']
result = []
for i in range(1, 4):
    for letter in letters:
        result.append(letter + str(i))
print(result)
```

#### Q2. The marks of a student in each subject given below. Write a Python/Scala function that takes two parameters 'name' and 'subjects_marks. Finally, print the student's name and all the subjects in which his/her marks are above 60. If the 'name' is not provided, print 'None.'

**Input:** Maths = 80, Physics = 58, Chemistry = 62, English = 72, Biology = 50

**Expected Output:** Name: Vishnu - Subjects: {'Chemistry', 'English', 'Mathematics"}

```python
def print_above_60(name='None', subjects_marks={}):
    if name == 'None':
        print(name)
        return
    
    above_60 = [subject for subject, mark in subjects_marks.items() if mark > 60]
    print(f"Name: {name} - Subjects: {above_60}")

marks = {'Maths': 80, 'Physics': 58, 'Chemistry': 62, 'English': 72, 'Biology': 50}
print_above_60(name="Vishnu", subjects_marks=marks)
```

#### Q3. Given list of companies with their face values in the stock market. Write a Python/Scala code to get the company's name along with its face value for the company, which has the maximum and the minimum face values. Also sort this list based on face values in increasing order.

stock_market = ('AXIS BANK': 7, 'BHARTI AIRTEL': 5,'COAL INDIA': 10,'ITC': 1, 'TCS': 3,'L&T': 2,'RELIANCE': 9, 'KOTAK BANK': 8,'AMERICAN EXPRESS': 11}

**Expected Output:**

(1, 'ITC')
(11, 'AMERICAN EXPRESS')

[(1, 'ITC'), (2, 'L&T'), (3, 'TCS'), (5, 'BHARTI AIRTEL"), (7, AXIS BANK'), (8, 'KOTAK BANK"), (9, 'RELIANCE), (10, 'COAL INDIA'), (11, 'AMERICAN EXPRESS')]

```python
stock_market = {'AXIS BANK': 7,
'BHARTI AIRTEL': 5,
'COAL INDIA': 10,
'ITC': 1,
'TCS': 3,
'L&T': 2,
'RELIANCE': 9,
'KOTAK BANK': 8,
'AMERICAN EXPRESS': 11}

min_val = min(stock_market.items(), key=lambda x: x[1])
max_val = max(stock_market.items(), key=lambda x: x[1])

print(min_val)
print(max_val)

sorted_list = sorted(stock_market.items(), key=lambda x: x[1])
print(sorted_list)
```
###  Q3. Write a Scala or Python Programme with two lists of integers as input, and returns a new list 

list_1 = [12, 25, 31, 20, 18]
list_2 = [11, 9, 43, 22, 55]

**Expected Output** : 
- 12 55
- 25 22
- 31 43
- 20 9
- 18 11

```python
list_1 = [12, 25, 31, 20, 18]
list_2 = [11, 9, 43, 22, 55]

for i, j in zip(list_1, reversed(list_2)):
    print(i,j)
 ```

