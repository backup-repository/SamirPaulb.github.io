---
title: 0612 Shortest Distance in a Plane
summary: 0612 Shortest Distance in a Plane LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["0612 Shortest Distance in a Plane LeetCode Solution Explained in all languages", "0612 Shortest Distance in a Plane", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0612 Shortest Distance in a Plane - Solution Explained/problem-solving.webp
    alt: 0612 Shortest Distance in a Plane
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [612. Shortest Distance in a Plane](https://leetcode.com/problems/shortest-distance-in-a-plane)


## Description

<p>Table: <code>Point2D</code></p>

<pre>
+-------------+------+
| Column Name | Type |
+-------------+------+
| x           | int  |
| y           | int  |
+-------------+------+
(x, y) is the primary key column (combination of columns with unique values) for this table.
Each row of this table indicates the position of a point on the X-Y plane.
</pre>

<p>&nbsp;</p>

<p>The distance between two points <code>p<sub>1</sub>(x<sub>1</sub>, y<sub>1</sub>)</code> and <code>p<sub>2</sub>(x<sub>2</sub>, y<sub>2</sub>)</code> is <code>sqrt((x<sub>2</sub> - x<sub>1</sub>)<sup>2</sup> + (y<sub>2</sub> - y<sub>1</sub>)<sup>2</sup>)</code>.</p>

<p>Write a solution to report the shortest distance between any two points from the <code>Point2D</code> table. Round the distance to <strong>two decimal points</strong>.</p>

<p>The&nbsp;result format is in the following example.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> 
Point2D table:
+----+----+
| x  | y  |
+----+----+
| -1 | -1 |
| 0  | 0  |
| -1 | -2 |
+----+----+
<strong>Output:</strong> 
+----------+
| shortest |
+----------+
| 1.00     |
+----------+
<strong>Explanation:</strong> The shortest distance is 1.00 from point (-1, -1) to (-1, 2).
</pre>

## Solutions

### Solution 1

<!-- tabs:start -->

```sql
# Write your MySQL query statement below
SELECT ROUND(SQRT(POW(p1.x - p2.x, 2) + POW(p1.y - p2.y, 2)), 2) AS shortest
FROM
    Point2D AS p1
    JOIN Point2D AS p2 ON p1.x != p2.x OR p1.y != p2.y
ORDER BY 1
LIMIT 1;
```

<!-- tabs:end -->

<!-- end -->
