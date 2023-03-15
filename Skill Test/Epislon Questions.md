## Epislon Skil Test - Python (Programming Language)

#### Q1. Food Stalls

Robin goes to a food festival along with N-1 friends. Robin is labeled as 1 and his friends are labeled from 2 to N. 
Each of them has a set of colored coupons. The food festival has M food stalls numbered from 1 to M. 
Every food stall accepts particular color coupons only.

There are 10 different color coupons represented by numbers ranging from 1 to 10. You are given certain number of queries Q. 
Find the sum of the outputs of all the queries.

**Input Specification:**

- *input1:* N, total size of the group of friends including Robin
- *input2:* M, number of stalls
- *input3:* A two dimensional array of size M * 10, where cell(i, j) = 1 denotes that stall i accepts coupon j
- *input4:* A two dimensional array of size N * 10, where cell(i, j) = 1 denotes that person i has coupon j
- *input5:* Q, number of queries
- *input6:* A two dimensional array of size Q* 2, containing sets for which the query

All has to be answered. For each row [i, j], if person i can eat at stall j, then output of the query is 1 else output is 0

**Output Specification:**
Your function should return the sum of the output of all the queries.

```python
def food_stalls_func(N, M, food_stalls_data, coupons, Q, queries):
    result = 0
    for i in range(Q):
        person, stall = queries[i]
        for j in range(10):
            if coupons[person - 1][j] == 1 and food_stalls_data[stall - 1][j] == 1:
                result += 1
                break
    return result

N = 5
M = 3
food_stalls_data = [[1, 1, 1, 0, 0, 0, 0, 0, 0, 0], [0, 0, 0, 1, 1, 0, 0, 0, 0, 0], [0, 0, 0, 0, 0, 1, 1, 1, 1, 1]]
coupons = [[1, 1, 1, 0, 0, 0, 0, 0, 0, 0], [0, 0, 0, 1, 1, 0, 0, 0, 0, 0], [1, 1, 1, 0, 0, 0, 0, 0, 0, 0], [0, 0, 0, 1, 1, 1, 1, 1, 1, 1], [1, 1, 1, 1, 1, 1, 1, 1, 1, 1]]
Q = 5
queries = [[1, 1], [2, 2], [3, 3], [4, 1], [5, 2]]

print(food_stalls_func(N, M, food_stalls_data, coupons, Q, queries))

```

#### Q2. Lost In The Forest - Python 

A boy is lost in an infinitely long 1 dimensional jungle. The jungle is such that if the boy is standing at location N, 
then, after the next step he would be moved to location (N/2) if N is even, and (3N + 1) if N is odd.
However, there is a magic door in the jungle that can take him to any location N he wants to go between location 1 and M (including both), but just once.

Find the location that the boy should go to such that he reaches the maximum number of locations in the forest.

 **Input Specification:**
 
- *input1:* The value of M

**Output Specification:**

Return the location where the boy should go first. If there are multiple answers, then return the largest one.

** Example **
- input1: 5
- Output: 3

```python
    def lostInForest(cls, input1):
        def max_locations(m):
            max_loc = 0
            max_start = 0
            for i in range(1, m+1):
                location = i
                count = 1
                while location != 1:
                    if location % 2 == 0:
                        location = location / 2
                    else:
                        location = 3 * location + 1
                    count += 1
                if count > max_loc:
                    max_loc = count
                    max_start = i
            return max_start

        return max_locations(input1)

print(UserMainCode.lostInForest(5)) 

```
