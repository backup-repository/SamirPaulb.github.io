---
title: 2352 Equal Row and Column Pairs
summary: 2352 Equal Row and Column Pairs LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["2352 Equal Row and Column Pairs LeetCode Solution Explained in all languages", "2352 Equal Row and Column Pairs", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:2352 Equal Row and Column Pairs - Solution Explained/problem-solving.webp
    alt: 2352 Equal Row and Column Pairs
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [2352. Equal Row and Column Pairs](https://leetcode.com/problems/equal-row-and-column-pairs)


## Description

<p>Given a <strong>0-indexed</strong> <code>n x n</code> integer matrix <code>grid</code>, <em>return the number of pairs </em><code>(r<sub>i</sub>, c<sub>j</sub>)</code><em> such that row </em><code>r<sub>i</sub></code><em> and column </em><code>c<sub>j</sub></code><em> are equal</em>.</p>

<p>A row and column pair is considered equal if they contain the same elements in the same order (i.e., an equal array).</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<img alt="" src="https://spcdn.pages.dev/leetcode/problems/2352.Equal%20Row%20and%20Column%20Pairs/images/ex1.jpg" style="width: 150px; height: 153px;" />
<pre>
<strong>Input:</strong> grid = [[3,2,1],[1,7,6],[2,7,7]]
<strong>Output:</strong> 1
<strong>Explanation:</strong> There is 1 equal row and column pair:
- (Row 2, Column 1): [2,7,7]
</pre>

<p><strong class="example">Example 2:</strong></p>
<img alt="" src="https://spcdn.pages.dev/leetcode/problems/2352.Equal%20Row%20and%20Column%20Pairs/images/ex2.jpg" style="width: 200px; height: 209px;" />
<pre>
<strong>Input:</strong> grid = [[3,1,2,2],[1,4,4,5],[2,4,2,2],[2,4,2,2]]
<strong>Output:</strong> 3
<strong>Explanation:</strong> There are 3 equal row and column pairs:
- (Row 0, Column 0): [3,1,2,2]
- (Row 2, Column 2): [2,4,2,2]
- (Row 3, Column 2): [2,4,2,2]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == grid.length == grid[i].length</code></li>
	<li><code>1 &lt;= n &lt;= 200</code></li>
	<li><code>1 &lt;= grid[i][j] &lt;= 10<sup>5</sup></code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def equalPairs(self, grid: List[List[int]]) -> int:
        g = [list(col) for col in zip(*grid)]
        return sum(row == col for row in grid for col in g)
```

```java
class Solution {
    public int equalPairs(int[][] grid) {
        int n = grid.length;
        int[][] g = new int[n][n];
        for (int j = 0; j < n; ++j) {
            for (int i = 0; i < n; ++i) {
                g[i][j] = grid[j][i];
            }
        }
        int ans = 0;
        for (var row : grid) {
            for (var col : g) {
                int ok = 1;
                for (int i = 0; i < n; ++i) {
                    if (row[i] != col[i]) {
                        ok = 0;
                        break;
                    }
                }
                ans += ok;
            }
        }
        return ans;
    }
}
```

```cpp
class Solution {
public:
    int equalPairs(vector<vector<int>>& grid) {
        int n = grid.size();
        vector<vector<int>> g(n, vector<int>(n));
        for (int j = 0; j < n; ++j) {
            for (int i = 0; i < n; ++i) {
                g[i][j] = grid[j][i];
            }
        }
        int ans = 0;
        for (auto& row : grid) {
            for (auto& col : g) {
                ans += row == col;
            }
        }
        return ans;
    }
};
```

```go
func equalPairs(grid [][]int) (ans int) {
	n := len(grid)
	g := make([][]int, n)
	for i := range g {
		g[i] = make([]int, n)
		for j := 0; j < n; j++ {
			g[i][j] = grid[j][i]
		}
	}
	for _, row := range grid {
		for _, col := range g {
			ok := 1
			for i, v := range row {
				if v != col[i] {
					ok = 0
					break
				}
			}
			ans += ok
		}
	}
	return
}
```

```ts
function equalPairs(grid: number[][]): number {
    const n = grid.length;
    const g = Array.from({ length: n }, () => Array.from({ length: n }, () => 0));
    for (let j = 0; j < n; ++j) {
        for (let i = 0; i < n; ++i) {
            g[i][j] = grid[j][i];
        }
    }
    let ans = 0;
    for (const row of grid) {
        for (const col of g) {
            ans += Number(row.toString() === col.toString());
        }
    }
    return ans;
}
```

<!-- tabs:end -->

### Solution 2

<!-- tabs:start -->

```python
class Solution:
    def equalPairs(self, grid: List[List[int]]) -> int:
        n = len(grid)
        ans = 0
        for i in range(n):
            for j in range(n):
                ans += all(grid[i][k] == grid[k][j] for k in range(n))
        return ans
```

```java
class Solution {
    public int equalPairs(int[][] grid) {
        int n = grid.length;
        int ans = 0;
        for (int i = 0; i < n; ++i) {
            for (int j = 0; j < n; ++j) {
                int ok = 1;
                for (int k = 0; k < n; ++k) {
                    if (grid[i][k] != grid[k][j]) {
                        ok = 0;
                        break;
                    }
                }
                ans += ok;
            }
        }
        return ans;
    }
}
```

```cpp
class Solution {
public:
    int equalPairs(vector<vector<int>>& grid) {
        int n = grid.size();
        int ans = 0;
        for (int i = 0; i < n; ++i) {
            for (int j = 0; j < n; ++j) {
                int ok = 1;
                for (int k = 0; k < n; ++k) {
                    if (grid[i][k] != grid[k][j]) {
                        ok = 0;
                        break;
                    }
                }
                ans += ok;
            }
        }
        return ans;
    }
};
```

```go
func equalPairs(grid [][]int) (ans int) {
	for i := range grid {
		for j := range grid {
			ok := 1
			for k := range grid {
				if grid[i][k] != grid[k][j] {
					ok = 0
					break
				}
			}
			ans += ok
		}
	}
	return
}
```

```ts
function equalPairs(grid: number[][]): number {
    const n = grid.length;
    let ans = 0;
    for (let i = 0; i < n; ++i) {
        for (let j = 0; j < n; ++j) {
            let ok = 1;
            for (let k = 0; k < n; ++k) {
                if (grid[i][k] !== grid[k][j]) {
                    ok = 0;
                    break;
                }
            }
            ans += ok;
        }
    }
    return ans;
}
```

<!-- tabs:end -->

<!-- end -->
