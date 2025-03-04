---
title: 0197 Rising Temperature
summary: 0197 Rising Temperature LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["0197 Rising Temperature LeetCode Solution Explained in all languages", "0197 Rising Temperature", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0197 Rising Temperature - Solution Explained/problem-solving.webp
    alt: 0197 Rising Temperature
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [197. Rising Temperature](https://leetcode.com/problems/rising-temperature)


## Description

<p>Table: <code>Weather</code></p>

<pre>
+---------------+---------+
| Column Name   | Type    |
+---------------+---------+
| id            | int     |
| recordDate    | date    |
| temperature   | int     |
+---------------+---------+
id is the column with unique values for this table.
This table contains information about the temperature on a certain day.
</pre>

<p>&nbsp;</p>

<p>Write a solution to find all dates&#39; <code>Id</code> with higher temperatures compared to its previous dates (yesterday).</p>

<p>Return the result table in <strong>any order</strong>.</p>

<p>The result format is in the following example.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> 
Weather table:
+----+------------+-------------+
| id | recordDate | temperature |
+----+------------+-------------+
| 1  | 2015-01-01 | 10          |
| 2  | 2015-01-02 | 25          |
| 3  | 2015-01-03 | 20          |
| 4  | 2015-01-04 | 30          |
+----+------------+-------------+
<strong>Output:</strong> 
+----+
| id |
+----+
| 2  |
| 4  |
+----+
<strong>Explanation:</strong> 
In 2015-01-02, the temperature was higher than the previous day (10 -&gt; 25).
In 2015-01-04, the temperature was higher than the previous day (20 -&gt; 30).
</pre>

## Solutions

### Solution 1: Self-Join + DATEDIFF/SUBDATE Function

We can use self-join to compare each row in the `Weather` table with its previous row. If the temperature is higher and the date difference is one day, then it is the result we are looking for.

<!-- tabs:start -->

```python
import pandas as pd


def rising_temperature(weather: pd.DataFrame) -> pd.DataFrame:
    weather.sort_values(by="recordDate", inplace=True)
    return weather[
        (weather.temperature.diff() > 0) & (weather.recordDate.diff().dt.days == 1)
    ][["id"]]
```

```sql
# Write your MySQL query statement below
SELECT w1.id
FROM
    Weather AS w1
    JOIN Weather AS w2
        ON DATEDIFF(w1.recordDate, w2.recordDate) = 1 AND w1.temperature > w2.temperature;
```

<!-- tabs:end -->

### Solution 2

<!-- tabs:start -->

```sql
# Write your MySQL query statement below
SELECT w1.id
FROM
    Weather AS w1
    JOIN Weather AS w2
        ON SUBDATE(w1.recordDate, 1) = w2.recordDate AND w1.temperature > w2.temperature;
```

<!-- tabs:end -->

<!-- end -->
