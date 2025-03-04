---
title: 1940 Longest Common Subsequence Between Sorted Arrays
summary: 1940 Longest Common Subsequence Between Sorted Arrays LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["1940 Longest Common Subsequence Between Sorted Arrays LeetCode Solution Explained in all languages", "1940 Longest Common Subsequence Between Sorted Arrays", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1940 Longest Common Subsequence Between Sorted Arrays - Solution Explained/problem-solving.webp
    alt: 1940 Longest Common Subsequence Between Sorted Arrays
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1940. Longest Common Subsequence Between Sorted Arrays](https://leetcode.com/problems/longest-common-subsequence-between-sorted-arrays)


## Description

<p>Given an array of integer arrays <code>arrays</code> where each <code>arrays[i]</code> is sorted in <strong>strictly increasing</strong> order, return <em>an integer array representing the <strong>longest common subsequence</strong> between <strong>all</strong> the arrays</em>.</p>

<p>A <strong>subsequence</strong> is a sequence that can be derived from another sequence by deleting some elements (possibly none) without changing the order of the remaining elements.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> arrays = [[<u>1</u>,3,<u>4</u>],
                 [<u>1</u>,<u>4</u>,7,9]]
<strong>Output:</strong> [1,4]
<strong>Explanation:</strong> The longest common subsequence in the two arrays is [1,4].
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> arrays = [[<u>2</u>,<u>3</u>,<u>6</u>,8],
                 [1,<u>2</u>,<u>3</u>,5,<u>6</u>,7,10],
                 [<u>2</u>,<u>3</u>,4,<u>6</u>,9]]
<strong>Output:</strong> [2,3,6]
<strong>Explanation:</strong> The longest common subsequence in all three arrays is [2,3,6].
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> arrays = [[1,2,3,4,5],
                 [6,7,8]]
<strong>Output:</strong> []
<strong>Explanation:</strong> There is no common subsequence between the two arrays.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>2 &lt;= arrays.length &lt;= 100</code></li>
	<li><code>1 &lt;= arrays[i].length &lt;= 100</code></li>
	<li><code>1 &lt;= arrays[i][j] &lt;= 100</code></li>
	<li><code>arrays[i]</code> is sorted in <strong>strictly increasing</strong> order.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def longestCommomSubsequence(self, arrays: List[List[int]]) -> List[int]:
        n = len(arrays)
        counter = defaultdict(int)
        for array in arrays:
            for e in array:
                counter[e] += 1
        return [e for e, count in counter.items() if count == n]
```

```java
class Solution {
    public List<Integer> longestCommomSubsequence(int[][] arrays) {
        Map<Integer, Integer> counter = new HashMap<>();
        for (int[] array : arrays) {
            for (int e : array) {
                counter.put(e, counter.getOrDefault(e, 0) + 1);
            }
        }
        int n = arrays.length;
        List<Integer> res = new ArrayList<>();
        for (Map.Entry<Integer, Integer> entry : counter.entrySet()) {
            if (entry.getValue() == n) {
                res.add(entry.getKey());
            }
        }
        return res;
    }
}
```

```cpp
class Solution {
public:
    vector<int> longestCommomSubsequence(vector<vector<int>>& arrays) {
        unordered_map<int, int> counter;
        vector<int> res;
        int n = arrays.size();
        for (auto array : arrays) {
            for (auto e : array) {
                counter[e] += 1;
                if (counter[e] == n) {
                    res.push_back(e);
                }
            }
        }
        return res;
    }
};
```

```go
func longestCommomSubsequence(arrays [][]int) []int {
	counter := make(map[int]int)
	n := len(arrays)
	var res []int
	for _, array := range arrays {
		for _, e := range array {
			counter[e]++
			if counter[e] == n {
				res = append(res, e)
			}
		}
	}
	return res
}
```

```js
/**
 * @param {number[][]} arrays
 * @return {number[]}
 */
var longestCommonSubsequence = function (arrays) {
    const m = new Map();
    const rs = [];
    const len = arrays.length;
    for (let i = 0; i < len; i++) {
        for (let j = 0; j < arrays[i].length; j++) {
            m.set(arrays[i][j], (m.get(arrays[i][j]) || 0) + 1);
            if (m.get(arrays[i][j]) === len) rs.push(arrays[i][j]);
        }
    }
    return rs;
};
```

<!-- tabs:end -->

### Solution 2

<!-- tabs:start -->

```python
class Solution:
    def longestCommomSubsequence(self, arrays: List[List[int]]) -> List[int]:
        def common(l1, l2):
            i, j, n1, n2 = 0, 0, len(l1), len(l2)
            res = []
            while i < n1 and j < n2:
                if l1[i] == l2[j]:
                    res.append(l1[i])
                    i += 1
                    j += 1
                elif l1[i] > l2[j]:
                    j += 1
                else:
                    i += 1
            return res

        n = len(arrays)
        for i in range(1, n):
            arrays[i] = common(arrays[i - 1], arrays[i])
        return arrays[n - 1]
```

<!-- tabs:end -->

<!-- end -->
