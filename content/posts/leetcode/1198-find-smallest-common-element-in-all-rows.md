---
title: 1198 Find Smallest Common Element in All Rows
summary: 1198 Find Smallest Common Element in All Rows LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["1198 Find Smallest Common Element in All Rows LeetCode Solution Explained in all languages", "1198 Find Smallest Common Element in All Rows", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1198 Find Smallest Common Element in All Rows - Solution Explained/problem-solving.webp
    alt: 1198 Find Smallest Common Element in All Rows
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1198. Find Smallest Common Element in All Rows](https://leetcode.com/problems/find-smallest-common-element-in-all-rows)


## Description

<p>Given an <code>m x n</code> matrix <code>mat</code> where every row is sorted in <strong>strictly</strong> <strong>increasing</strong> order, return <em>the <strong>smallest common element</strong> in all rows</em>.</p>

<p>If there is no common element, return <code>-1</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> mat = [[1,2,3,4,5],[2,4,5,8,10],[3,5,7,9,11],[1,3,5,7,9]]
<strong>Output:</strong> 5
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> mat = [[1,2,3],[2,3,4],[2,3,5]]
<strong>Output:</strong> 2
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>m == mat.length</code></li>
	<li><code>n == mat[i].length</code></li>
	<li><code>1 &lt;= m, n &lt;= 500</code></li>
	<li><code>1 &lt;= mat[i][j] &lt;= 10<sup>4</sup></code></li>
	<li><code>mat[i]</code> is sorted in strictly increasing order.</li>
</ul>

## Solutions

### Solution 1: Counting

We use an array $cnt$ of length $10001$ to count the frequency of each number. We sequentially traverse each number in the matrix and increment its frequency. When the frequency of a number equals the number of rows in the matrix, it means that this number appears in each row, and thus it is the smallest common element. We return this number.

If we do not find the smallest common element after the traversal, we return $-1$.

The time complexity is $O(m \times n)$, and the space complexity is $O(10^4)$. Here, $m$ and $n$ are the number of rows and columns in the matrix, respectively.

<!-- tabs:start -->

```python
class Solution:
    def smallestCommonElement(self, mat: List[List[int]]) -> int:
        cnt = Counter()
        for row in mat:
            for x in row:
                cnt[x] += 1
                if cnt[x] == len(mat):
                    return x
        return -1
```

```java
class Solution {
    public int smallestCommonElement(int[][] mat) {
        int[] cnt = new int[10001];
        for (var row : mat) {
            for (int x : row) {
                if (++cnt[x] == mat.length) {
                    return x;
                }
            }
        }
        return -1;
    }
}
```

```cpp
class Solution {
public:
    int smallestCommonElement(vector<vector<int>>& mat) {
        int cnt[10001]{};
        for (auto& row : mat) {
            for (int x : row) {
                if (++cnt[x] == mat.size()) {
                    return x;
                }
            }
        }
        return -1;
    }
};
```

```go
func smallestCommonElement(mat [][]int) int {
	cnt := [10001]int{}
	for _, row := range mat {
		for _, x := range row {
			cnt[x]++
			if cnt[x] == len(mat) {
				return x
			}
		}
	}
	return -1
}
```

```ts
function smallestCommonElement(mat: number[][]): number {
    const cnt: number[] = new Array(10001).fill(0);
    for (const row of mat) {
        for (const x of row) {
            if (++cnt[x] == mat.length) {
                return x;
            }
        }
    }
    return -1;
}
```

<!-- tabs:end -->

<!-- end -->
