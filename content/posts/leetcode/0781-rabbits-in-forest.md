---
title: 0781 Rabbits in Forest
summary: 0781 Rabbits in Forest LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["0781 Rabbits in Forest LeetCode Solution Explained in all languages", "0781 Rabbits in Forest", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0781 Rabbits in Forest - Solution Explained/problem-solving.webp
    alt: 0781 Rabbits in Forest
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [781. Rabbits in Forest](https://leetcode.com/problems/rabbits-in-forest)


## Description

<p>There is a forest with an unknown number of rabbits. We asked n rabbits <strong>&quot;How many rabbits have the same color as you?&quot;</strong> and collected the answers in an integer array <code>answers</code> where <code>answers[i]</code> is the answer of the <code>i<sup>th</sup></code> rabbit.</p>

<p>Given the array <code>answers</code>, return <em>the minimum number of rabbits that could be in the forest</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> answers = [1,1,2]
<strong>Output:</strong> 5
<strong>Explanation:</strong>
The two rabbits that answered &quot;1&quot; could both be the same color, say red.
The rabbit that answered &quot;2&quot; can&#39;t be red or the answers would be inconsistent.
Say the rabbit that answered &quot;2&quot; was blue.
Then there should be 2 other blue rabbits in the forest that didn&#39;t answer into the array.
The smallest possible number of rabbits in the forest is therefore 5: 3 that answered plus 2 that didn&#39;t.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> answers = [10,10,10]
<strong>Output:</strong> 11
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= answers.length &lt;= 1000</code></li>
	<li><code>0 &lt;= answers[i] &lt; 1000</code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def numRabbits(self, answers: List[int]) -> int:
        counter = Counter(answers)
        return sum([math.ceil(v / (k + 1)) * (k + 1) for k, v in counter.items()])
```

```java
class Solution {
    public int numRabbits(int[] answers) {
        Map<Integer, Integer> counter = new HashMap<>();
        for (int e : answers) {
            counter.put(e, counter.getOrDefault(e, 0) + 1);
        }
        int res = 0;
        for (Map.Entry<Integer, Integer> entry : counter.entrySet()) {
            int answer = entry.getKey(), count = entry.getValue();
            res += (int) Math.ceil(count / ((answer + 1) * 1.0)) * (answer + 1);
        }
        return res;
    }
}
```

<!-- tabs:end -->

<!-- end -->
