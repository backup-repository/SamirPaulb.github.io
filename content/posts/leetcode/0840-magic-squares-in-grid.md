---
title: 0840 Magic Squares In Grid
summary: 0840 Magic Squares In Grid LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["0840 Magic Squares In Grid LeetCode Solution Explained in all languages", "0840 Magic Squares In Grid", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0840 Magic Squares In Grid - Solution Explained/problem-solving.webp
    alt: 0840 Magic Squares In Grid
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [840. Magic Squares In Grid](https://leetcode.com/problems/magic-squares-in-grid)


## Description

<p>A <code>3 x 3</code> magic square is a <code>3 x 3</code> grid filled with distinct numbers <strong>from </strong><code>1</code><strong> to </strong><code>9</code> such that each row, column, and both diagonals all have the same sum.</p>

<p>Given a <code>row x col</code>&nbsp;<code>grid</code>&nbsp;of integers, how many <code>3 x 3</code> &quot;magic square&quot; subgrids are there?&nbsp; (Each subgrid is contiguous).</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<img alt="" src="https://spcdn.pages.dev/leetcode/problems/0840.Magic%20Squares%20In%20Grid/images/magic_main.jpg" style="width: 322px; height: 242px;" />
<pre>
<strong>Input:</strong> grid = [[4,3,8,4],[9,5,1,9],[2,7,6,2]]
<strong>Output:</strong> 1
<strong>Explanation: </strong>
The following subgrid is a 3 x 3 magic square:
<img alt="" src="https://spcdn.pages.dev/leetcode/problems/0840.Magic%20Squares%20In%20Grid/images/magic_valid.jpg" style="width: 242px; height: 242px;" />
while this one is not:
<img alt="" src="https://spcdn.pages.dev/leetcode/problems/0840.Magic%20Squares%20In%20Grid/images/magic_invalid.jpg" style="width: 242px; height: 242px;" />
In total, there is only one magic square inside the given grid.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> grid = [[8]]
<strong>Output:</strong> 0
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>row == grid.length</code></li>
	<li><code>col == grid[i].length</code></li>
	<li><code>1 &lt;= row, col &lt;= 10</code></li>
	<li><code>0 &lt;= grid[i][j] &lt;= 15</code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def numMagicSquaresInside(self, grid: List[List[int]]) -> int:
        def check(i: int, j: int) -> int:
            if i + 3 > m or j + 3 > n:
                return 0
            s = set()
            row = [0] * 3
            col = [0] * 3
            a = b = 0
            for x in range(i, i + 3):
                for y in range(j, j + 3):
                    v = grid[x][y]
                    if v < 1 or v > 9:
                        return 0
                    s.add(v)
                    row[x - i] += v
                    col[y - j] += v
                    if x - i == y - j:
                        a += v
                    if x - i == 2 - (y - j):
                        b += v
            if len(s) != 9 or a != b:
                return 0
            if any(x != a for x in row) or any(x != a for x in col):
                return 0
            return 1

        m, n = len(grid), len(grid[0])
        return sum(check(i, j) for i in range(m) for j in range(n))
```

```java
class Solution {
    private int m;
    private int n;
    private int[][] grid;

    public int numMagicSquaresInside(int[][] grid) {
        m = grid.length;
        n = grid[0].length;
        this.grid = grid;
        int ans = 0;
        for (int i = 0; i < m; ++i) {
            for (int j = 0; j < n; ++j) {
                ans += check(i, j);
            }
        }
        return ans;
    }

    private int check(int i, int j) {
        if (i + 3 > m || j + 3 > n) {
            return 0;
        }
        int[] cnt = new int[16];
        int[] row = new int[3];
        int[] col = new int[3];
        int a = 0, b = 0;
        for (int x = i; x < i + 3; ++x) {
            for (int y = j; y < j + 3; ++y) {
                int v = grid[x][y];
                if (v < 1 || v > 9 || ++cnt[v] > 1) {
                    return 0;
                }
                row[x - i] += v;
                col[y - j] += v;
                if (x - i == y - j) {
                    a += v;
                }
                if (x - i + y - j == 2) {
                    b += v;
                }
            }
        }
        if (a != b) {
            return 0;
        }
        for (int k = 0; k < 3; ++k) {
            if (row[k] != a || col[k] != a) {
                return 0;
            }
        }
        return 1;
    }
}
```

```cpp
class Solution {
public:
    int numMagicSquaresInside(vector<vector<int>>& grid) {
        int m = grid.size();
        int n = grid[0].size();
        int ans = 0;
        auto check = [&](int i, int j) {
            if (i + 3 > m || j + 3 > n) {
                return 0;
            }
            vector<int> cnt(16);
            vector<int> row(3);
            vector<int> col(3);
            int a = 0, b = 0;
            for (int x = i; x < i + 3; ++x) {
                for (int y = j; y < j + 3; ++y) {
                    int v = grid[x][y];
                    if (v < 1 || v > 9 || ++cnt[v] > 1) {
                        return 0;
                    }
                    row[x - i] += v;
                    col[y - j] += v;
                    if (x - i == y - j) {
                        a += v;
                    }
                    if (x - i + y - j == 2) {
                        b += v;
                    }
                }
            }
            if (a != b) {
                return 0;
            }
            for (int k = 0; k < 3; ++k) {
                if (row[k] != a || col[k] != a) {
                    return 0;
                }
            }
            return 1;
        };
        for (int i = 0; i < m; ++i) {
            for (int j = 0; j < n; ++j) {
                ans += check(i, j);
            }
        }
        return ans;
    }
};
```

```go
func numMagicSquaresInside(grid [][]int) (ans int) {
	m, n := len(grid), len(grid[0])
	check := func(i, j int) int {
		if i+3 > m || j+3 > n {
			return 0
		}
		cnt := [16]int{}
		row := [3]int{}
		col := [3]int{}
		a, b := 0, 0
		for x := i; x < i+3; x++ {
			for y := j; y < j+3; y++ {
				v := grid[x][y]
				if v < 1 || v > 9 || cnt[v] > 0 {
					return 0
				}
				cnt[v]++
				row[x-i] += v
				col[y-j] += v
				if x-i == y-j {
					a += v
				}
				if x-i == 2-(y-j) {
					b += v
				}
			}
		}
		if a != b {
			return 0
		}
		for k := 0; k < 3; k++ {
			if row[k] != a || col[k] != a {
				return 0
			}
		}
		return 1
	}
	for i := 0; i < m; i++ {
		for j := 0; j < n; j++ {
			ans += check(i, j)
		}
	}
	return
}
```

```ts
function numMagicSquaresInside(grid: number[][]): number {
    const m = grid.length;
    const n = grid[0].length;
    const check = (i: number, j: number): number => {
        if (i + 3 > m || j + 3 > n) {
            return 0;
        }
        const cnt: number[] = new Array(16).fill(0);
        const row: number[] = new Array(3).fill(0);
        const col: number[] = new Array(3).fill(0);
        let [a, b] = [0, 0];
        for (let x = i; x < i + 3; ++x) {
            for (let y = j; y < j + 3; ++y) {
                const v = grid[x][y];
                if (v < 1 || v > 9 || ++cnt[v] > 1) {
                    return 0;
                }
                row[x - i] += v;
                col[y - j] += v;
                if (x - i === y - j) {
                    a += v;
                }
                if (x - i === 2 - (y - j)) {
                    b += v;
                }
            }
        }
        if (a !== b) {
            return 0;
        }
        for (let k = 0; k < 3; ++k) {
            if (row[k] !== a || col[k] !== a) {
                return 0;
            }
        }
        return 1;
    };
    let ans = 0;
    for (let i = 0; i < m; ++i) {
        for (let j = 0; j < n; ++j) {
            ans += check(i, j);
        }
    }
    return ans;
}
```

<!-- tabs:end -->

<!-- end -->
