---
title: 1683 Invalid Tweets
summary: 1683 Invalid Tweets LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["1683 Invalid Tweets LeetCode Solution Explained in all languages", "1683 Invalid Tweets", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1683 Invalid Tweets - Solution Explained/problem-solving.webp
    alt: 1683 Invalid Tweets
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1683. Invalid Tweets](https://leetcode.com/problems/invalid-tweets)


## Description

<p>Table: <code>Tweets</code></p>

<pre>
+----------------+---------+
| Column Name    | Type    |
+----------------+---------+
| tweet_id       | int     |
| content        | varchar |
+----------------+---------+
tweet_id is the primary key (column with unique values) for this table.
This table contains all the tweets in a social media app.
</pre>

<p>&nbsp;</p>

<p>Write a solution to find the IDs of the invalid tweets. The tweet is invalid if the number of characters used in the content of the tweet is <strong>strictly greater</strong> than <code>15</code>.</p>

<p>Return the result table in <strong>any order</strong>.</p>

<p>The result format is in the following example.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> 
Tweets table:
+----------+----------------------------------+
| tweet_id | content                          |
+----------+----------------------------------+
| 1        | Vote for Biden                   |
| 2        | Let us make America great again! |
+----------+----------------------------------+
<strong>Output:</strong> 
+----------+
| tweet_id |
+----------+
| 2        |
+----------+
<strong>Explanation:</strong> 
Tweet 1 has length = 14. It is a valid tweet.
Tweet 2 has length = 32. It is an invalid tweet.
</pre>

## Solutions

### Solution 1: Using `CHAR_LENGTH` Function

The `CHAR_LENGTH()` function returns the length of a string, where Chinese characters, numbers, and letters are all counted as $1$ byte.

The `LENGTH()` function returns the length of a string, where under utf8 encoding, Chinese characters are counted as $3$ bytes, while numbers and letters are counted as $1$ byte; under gbk encoding, Chinese characters are counted as $2$ bytes, while numbers and letters are counted as $1$ byte.

For this problem, we can directly use the `CHAR_LENGTH` function to get the length of the string, and filter out the tweet IDs with a length greater than $15$.

<!-- tabs:start -->

```sql
# Write your MySQL query statement below
SELECT
    tweet_id
FROM Tweets
WHERE CHAR_LENGTH(content) > 15;
```

<!-- tabs:end -->

<!-- end -->
