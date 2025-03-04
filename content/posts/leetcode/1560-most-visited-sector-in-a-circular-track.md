---
title: 1560 Most Visited Sector in a Circular Track
summary: 1560 Most Visited Sector in a Circular Track LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["1560 Most Visited Sector in a Circular Track LeetCode Solution Explained in all languages", "1560 Most Visited Sector in a Circular Track", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1560 Most Visited Sector in a Circular Track - Solution Explained/problem-solving.webp
    alt: 1560 Most Visited Sector in a Circular Track
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1560. Most Visited Sector in a Circular Track](https://leetcode.com/problems/most-visited-sector-in-a-circular-track)


## Description

<p>Given an integer <code>n</code> and an integer array <code>rounds</code>. We have a circular track which consists of <code>n</code> sectors labeled from <code>1</code> to <code>n</code>. A marathon will be held on this track, the marathon consists of <code>m</code> rounds. The <code>i<sup>th</sup></code> round starts at sector <code>rounds[i - 1]</code> and ends at sector <code>rounds[i]</code>. For example, round 1 starts at sector <code>rounds[0]</code> and ends at sector <code>rounds[1]</code></p>

<p>Return <em>an array of the most visited sectors</em> sorted in <strong>ascending</strong> order.</p>

<p>Notice that you circulate the track in ascending order of sector numbers in the counter-clockwise direction (See the first example).</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<img alt="" src="https://spcdn.pages.dev/leetcode/problems/1560.Most%20Visited%20Sector%20in%20%20a%20Circular%20Track/images/tmp.jpg" style="width: 433px; height: 341px;" />
<pre>
<strong>Input:</strong> n = 4, rounds = [1,3,1,2]
<strong>Output:</strong> [1,2]
<strong>Explanation:</strong> The marathon starts at sector 1. The order of the visited sectors is as follows:
1 --&gt; 2 --&gt; 3 (end of round 1) --&gt; 4 --&gt; 1 (end of round 2) --&gt; 2 (end of round 3 and the marathon)
We can see that both sectors 1 and 2 are visited twice and they are the most visited sectors. Sectors 3 and 4 are visited only once.</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = 2, rounds = [2,1,2,1,2,1,2,1,2]
<strong>Output:</strong> [2]
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> n = 7, rounds = [1,3,5,7]
<strong>Output:</strong> [1,2,3,4,5,6,7]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>2 &lt;= n &lt;= 100</code></li>
	<li><code>1 &lt;= m &lt;= 100</code></li>
	<li><code>rounds.length == m + 1</code></li>
	<li><code>1 &lt;= rounds[i] &lt;= n</code></li>
	<li><code>rounds[i] != rounds[i + 1]</code> for <code>0 &lt;= i &lt; m</code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def mostVisited(self, n: int, rounds: List[int]) -> List[int]:
        if rounds[0] <= rounds[-1]:
            return list(range(rounds[0], rounds[-1] + 1))
        return list(range(1, rounds[-1] + 1)) + list(range(rounds[0], n + 1))
```

```java
class Solution {
    public List<Integer> mostVisited(int n, int[] rounds) {
        int m = rounds.length - 1;
        List<Integer> ans = new ArrayList<>();
        if (rounds[0] <= rounds[m]) {
            for (int i = rounds[0]; i <= rounds[m]; ++i) {
                ans.add(i);
            }
        } else {
            for (int i = 1; i <= rounds[m]; ++i) {
                ans.add(i);
            }
            for (int i = rounds[0]; i <= n; ++i) {
                ans.add(i);
            }
        }
        return ans;
    }
}
```

```cpp
class Solution {
public:
    vector<int> mostVisited(int n, vector<int>& rounds) {
        int m = rounds.size() - 1;
        vector<int> ans;
        if (rounds[0] <= rounds[m]) {
            for (int i = rounds[0]; i <= rounds[m]; ++i) ans.push_back(i);
        } else {
            for (int i = 1; i <= rounds[m]; ++i) ans.push_back(i);
            for (int i = rounds[0]; i <= n; ++i) ans.push_back(i);
        }
        return ans;
    }
};
```

```go
func mostVisited(n int, rounds []int) []int {
	m := len(rounds) - 1
	var ans []int
	if rounds[0] <= rounds[m] {
		for i := rounds[0]; i <= rounds[m]; i++ {
			ans = append(ans, i)
		}
	} else {
		for i := 1; i <= rounds[m]; i++ {
			ans = append(ans, i)
		}
		for i := rounds[0]; i <= n; i++ {
			ans = append(ans, i)
		}
	}
	return ans
}
```

<!-- tabs:end -->

<!-- end -->
