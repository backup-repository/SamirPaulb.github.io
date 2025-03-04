---
title: 0182 Duplicate Emails
summary: 0182 Duplicate Emails LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["0182 Duplicate Emails LeetCode Solution Explained in all languages", "0182 Duplicate Emails", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0182 Duplicate Emails - Solution Explained/problem-solving.webp
    alt: 0182 Duplicate Emails
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [182. Duplicate Emails](https://leetcode.com/problems/duplicate-emails)


## Description

<p>Table: <code>Person</code></p>

<pre>
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| id          | int     |
| email       | varchar |
+-------------+---------+
id is the primary key (column with unique values) for this table.
Each row of this table contains an email. The emails will not contain uppercase letters.
</pre>

<p>&nbsp;</p>

<p>Write a solution to report all the duplicate emails. Note that it&#39;s guaranteed that the email&nbsp;field is not NULL.</p>

<p>Return the result table in <strong>any order</strong>.</p>

<p>The&nbsp;result format is in the following example.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> 
Person table:
+----+---------+
| id | email   |
+----+---------+
| 1  | a@b.com |
| 2  | c@d.com |
| 3  | a@b.com |
+----+---------+
<strong>Output:</strong> 
+---------+
| Email   |
+---------+
| a@b.com |
+---------+
<strong>Explanation:</strong> a@b.com is repeated two times.
</pre>

## Solutions

### Solution 1: Group By + Having

We can use the `GROUP BY` statement to group the data by the `email` field, and then use the `HAVING` statement to filter out the `email` addresses that appear more than once.

<!-- tabs:start -->

```python
import pandas as pd


def duplicate_emails(person: pd.DataFrame) -> pd.DataFrame:
    results = pd.DataFrame()

    results = person.loc[person.duplicated(subset=["email"]), ["email"]]

    return results.drop_duplicates()
```

```sql
# Write your MySQL query statement below
SELECT email
FROM Person
GROUP BY 1
HAVING COUNT(1) > 1;
```

<!-- tabs:end -->

### Solution 2: Self-Join

We can use a self-join to join the `Person` table with itself, and then filter out the records where the `id` is different but the `email` is the same.

<!-- tabs:start -->

```sql
SELECT DISTINCT p1.email
FROM
    person AS p1,
    person AS p2
WHERE p1.id != p2.id AND p1.email = p2.email;
```

<!-- tabs:end -->

<!-- end -->
