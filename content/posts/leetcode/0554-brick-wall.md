---
title: 0554 Brick Wall
summary: 0554 Brick Wall LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["0554 Brick Wall LeetCode Solution Explained in all languages", "0554 Brick Wall", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0554 Brick Wall - Solution Explained/problem-solving.webp
    alt: 0554 Brick Wall
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [554. Brick Wall](https://leetcode.com/problems/brick-wall)


## Description

<p>There is a rectangular brick wall in front of you with <code>n</code> rows of bricks. The <code>i<sup>th</sup></code> row has some number of bricks each of the same height (i.e., one unit) but they can be of different widths. The total width of each row is the same.</p>

<p>Draw a vertical line from the top to the bottom and cross the least bricks. If your line goes through the edge of a brick, then the brick is not considered as crossed. You cannot draw a line just along one of the two vertical edges of the wall, in which case the line will obviously cross no bricks.</p>

<p>Given the 2D array <code>wall</code> that contains the information about the wall, return <em>the minimum number of crossed bricks after drawing such a vertical line</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<img alt="" src="https://spcdn.pages.dev/leetcode/problems/0554.Brick%20Wall/images/cutwall-grid.jpg" style="width: 493px; height: 577px;" />
<pre>
<strong>Input:</strong> wall = [[1,2,2,1],[3,1,2],[1,3,2],[2,4],[3,1,2],[1,3,1,1]]
<strong>Output:</strong> 2
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> wall = [[1],[1],[1]]
<strong>Output:</strong> 3
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == wall.length</code></li>
	<li><code>1 &lt;= n &lt;= 10<sup>4</sup></code></li>
	<li><code>1 &lt;= wall[i].length &lt;= 10<sup>4</sup></code></li>
	<li><code>1 &lt;= sum(wall[i].length) &lt;= 2 * 10<sup>4</sup></code></li>
	<li><code>sum(wall[i])</code> is the same for each row <code>i</code>.</li>
	<li><code>1 &lt;= wall[i][j] &lt;= 2<sup>31</sup> - 1</code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def leastBricks(self, wall: List[List[int]]) -> int:
        cnt = defaultdict(int)
        for row in wall:
            width = 0
            for brick in row[:-1]:
                width += brick
                cnt[width] += 1
        if not cnt:
            return len(wall)
        return len(wall) - cnt[max(cnt, key=cnt.get)]
```

```java
class Solution {
    public int leastBricks(List<List<Integer>> wall) {
        Map<Integer, Integer> cnt = new HashMap<>();
        for (List<Integer> row : wall) {
            int width = 0;
            for (int i = 0, n = row.size() - 1; i < n; i++) {
                width += row.get(i);
                cnt.merge(width, 1, Integer::sum);
            }
        }
        int max = cnt.values().stream().max(Comparator.naturalOrder()).orElse(0);
        return wall.size() - max;
    }
}
```

```go
func leastBricks(wall [][]int) int {
	cnt := make(map[int]int)
	for _, row := range wall {
		width := 0
		for _, brick := range row[:len(row)-1] {
			width += brick
			cnt[width]++
		}
	}
	max := 0
	for _, v := range cnt {
		if v > max {
			max = v
		}
	}
	return len(wall) - max
}
```

```js
/**
 * @param {number[][]} wall
 * @return {number}
 */
var leastBricks = function (wall) {
    const cnt = new Map();
    for (const row of wall) {
        let width = 0;
        for (let i = 0, n = row.length - 1; i < n; ++i) {
            width += row[i];
            cnt.set(width, (cnt.get(width) || 0) + 1);
        }
    }
    let max = 0;
    for (const v of cnt.values()) {
        max = Math.max(max, v);
    }
    return wall.length - max;
};
```

<!-- tabs:end -->

<!-- end -->
