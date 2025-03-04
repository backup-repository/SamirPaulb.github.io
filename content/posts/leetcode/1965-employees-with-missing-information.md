---
title: 1965 Employees With Missing Information
summary: 1965 Employees With Missing Information LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["1965 Employees With Missing Information LeetCode Solution Explained in all languages", "1965 Employees With Missing Information", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1965 Employees With Missing Information - Solution Explained/problem-solving.webp
    alt: 1965 Employees With Missing Information
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1965. Employees With Missing Information](https://leetcode.com/problems/employees-with-missing-information)


## Description

<p>Table: <code>Employees</code></p>

<pre>
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| employee_id | int     |
| name        | varchar |
+-------------+---------+
employee_id is the column with unique values for this table.
Each row of this table indicates the name of the employee whose ID is employee_id.
</pre>

<p>&nbsp;</p>

<p>Table: <code>Salaries</code></p>

<pre>
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| employee_id | int     |
| salary      | int     |
+-------------+---------+
employee_id is the column with unique values for this table.
Each row of this table indicates the salary of the employee whose ID is employee_id.
</pre>

<p>&nbsp;</p>

<p>Write a solution to report the IDs of all the employees with <strong>missing information</strong>. The information of an employee is missing if:</p>

<ul>
	<li>The employee&#39;s <strong>name</strong> is missing, or</li>
	<li>The employee&#39;s <strong>salary</strong> is missing.</li>
</ul>

<p>Return the result table ordered by <code>employee_id</code> <strong>in ascending order</strong>.</p>

<p>The result format is in the following example.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> 
Employees table:
+-------------+----------+
| employee_id | name     |
+-------------+----------+
| 2           | Crew     |
| 4           | Haven    |
| 5           | Kristian |
+-------------+----------+
Salaries table:
+-------------+--------+
| employee_id | salary |
+-------------+--------+
| 5           | 76071  |
| 1           | 22517  |
| 4           | 63539  |
+-------------+--------+
<strong>Output:</strong> 
+-------------+
| employee_id |
+-------------+
| 1           |
| 2           |
+-------------+
<strong>Explanation:</strong> 
Employees 1, 2, 4, and 5 are working at this company.
The name of employee 1 is missing.
The salary of employee 2 is missing.
</pre>

## Solutions

### Solution 1: Subquery + Union

We can first find all `employee_id` that are not in the `Salaries` table from the `Employees` table, and then find all `employee_id` that are not in the `Employees` table from the `Salaries` table. Finally, we can combine the two results using the `UNION` operator, and sort the result by `employee_id`.

<!-- tabs:start -->

```sql
# Write your MySQL query statement below
SELECT employee_id
FROM Employees
WHERE employee_id NOT IN (SELECT employee_id FROM Salaries)
UNION
SELECT employee_id
FROM Salaries
WHERE employee_id NOT IN (SELECT employee_id FROM Employees)
ORDER BY 1;
```

<!-- tabs:end -->

<!-- end -->
