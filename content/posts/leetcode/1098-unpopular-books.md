---
title: 1098 Unpopular Books
summary: 1098 Unpopular Books LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["1098 Unpopular Books LeetCode Solution Explained in all languages", "1098 Unpopular Books", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1098 Unpopular Books - Solution Explained/problem-solving.webp
    alt: 1098 Unpopular Books
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1098. Unpopular Books](https://leetcode.com/problems/unpopular-books)


## Description

<p>Table: <code>Books</code></p>

<pre>
+----------------+---------+
| Column Name    | Type    |
+----------------+---------+
| book_id        | int     |
| name           | varchar |
| available_from | date    |
+----------------+---------+
book_id is the primary key (column with unique values) of this table.
</pre>

<p>&nbsp;</p>

<p>Table: <code>Orders</code></p>

<pre>
+----------------+---------+
| Column Name    | Type    |
+----------------+---------+
| order_id       | int     |
| book_id        | int     |
| quantity       | int     |
| dispatch_date  | date    |
+----------------+---------+
order_id is the primary key (column with unique values) of this table.
book_id is a foreign key (reference column) to the Books table.
</pre>

<p>&nbsp;</p>

<p>Write a solution to report&nbsp;the <strong>books</strong> that have sold <strong>less than </strong><code>10</code> copies in the last year, excluding books that have been available for less than one month from today. <strong>Assume today is </strong><code>2019-06-23</code>.</p>

<p>Return the result table in <strong>any order</strong>.</p>

<p>The result format is in the following example.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> 
Books table:
+---------+--------------------+----------------+
| book_id | name               | available_from |
+---------+--------------------+----------------+
| 1       | &quot;Kalila And Demna&quot; | 2010-01-01     |
| 2       | &quot;28 Letters&quot;       | 2012-05-12     |
| 3       | &quot;The Hobbit&quot;       | 2019-06-10     |
| 4       | &quot;13 Reasons Why&quot;   | 2019-06-01     |
| 5       | &quot;The Hunger Games&quot; | 2008-09-21     |
+---------+--------------------+----------------+
Orders table:
+----------+---------+----------+---------------+
| order_id | book_id | quantity | dispatch_date |
+----------+---------+----------+---------------+
| 1        | 1       | 2        | 2018-07-26    |
| 2        | 1       | 1        | 2018-11-05    |
| 3        | 3       | 8        | 2019-06-11    |
| 4        | 4       | 6        | 2019-06-05    |
| 5        | 4       | 5        | 2019-06-20    |
| 6        | 5       | 9        | 2009-02-02    |
| 7        | 5       | 8        | 2010-04-13    |
+----------+---------+----------+---------------+
<strong>Output:</strong> 
+-----------+--------------------+
| book_id   | name               |
+-----------+--------------------+
| 1         | &quot;Kalila And Demna&quot; |
| 2         | &quot;28 Letters&quot;       |
| 5         | &quot;The Hunger Games&quot; |
+-----------+--------------------+
</pre>

## Solutions

### Solution 1

<!-- tabs:start -->

```sql
# Write your MySQL query statement below
SELECT book_id, name
FROM
    Books
    LEFT JOIN Orders USING (book_id)
WHERE available_from < '2019-05-23'
GROUP BY 1
HAVING SUM(IF(dispatch_date >= '2018-06-23', quantity, 0)) < 10;
```

<!-- tabs:end -->

<!-- end -->
