---
title: 1282 Group the People Given the Group Size They Belong To
summary: 1282 Group the People Given the Group Size They Belong To LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["1282 Group the People Given the Group Size They Belong To LeetCode Solution Explained in all languages", "1282 Group the People Given the Group Size They Belong To", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1282 Group the People Given the Group Size They Belong To - Solution Explained/problem-solving.webp
    alt: 1282 Group the People Given the Group Size They Belong To
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1282. Group the People Given the Group Size They Belong To](https://leetcode.com/problems/group-the-people-given-the-group-size-they-belong-to)


## Description

<p>There are <code>n</code> people&nbsp;that are split into some unknown number of groups. Each person is labeled with a&nbsp;<strong>unique ID</strong>&nbsp;from&nbsp;<code>0</code>&nbsp;to&nbsp;<code>n - 1</code>.</p>

<p>You are given an integer array&nbsp;<code>groupSizes</code>, where <code>groupSizes[i]</code>&nbsp;is the size of the group that person&nbsp;<code>i</code>&nbsp;is in. For example, if&nbsp;<code>groupSizes[1] = 3</code>, then&nbsp;person&nbsp;<code>1</code>&nbsp;must be in a&nbsp;group of size&nbsp;<code>3</code>.</p>

<p>Return&nbsp;<em>a list of groups&nbsp;such that&nbsp;each person&nbsp;<code>i</code>&nbsp;is in a group of size&nbsp;<code>groupSizes[i]</code></em>.</p>

<p>Each person should&nbsp;appear in&nbsp;<strong>exactly one group</strong>,&nbsp;and every person must be in a group. If there are&nbsp;multiple answers, <strong>return any of them</strong>. It is <strong>guaranteed</strong> that there will be <strong>at least one</strong> valid solution for the given input.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> groupSizes = [3,3,3,3,3,1,3]
<strong>Output:</strong> [[5],[0,1,2],[3,4,6]]
<b>Explanation:</b> 
The first group is [5]. The size is 1, and groupSizes[5] = 1.
The second group is [0,1,2]. The size is 3, and groupSizes[0] = groupSizes[1] = groupSizes[2] = 3.
The third group is [3,4,6]. The size is 3, and groupSizes[3] = groupSizes[4] = groupSizes[6] = 3.
Other possible solutions are [[2,1,6],[5],[0,4,3]] and [[5],[0,6,2],[4,3,1]].
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> groupSizes = [2,1,3,3,3,2]
<strong>Output:</strong> [[1],[0,5],[2,3,4]]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>groupSizes.length == n</code></li>
	<li><code>1 &lt;= n&nbsp;&lt;= 500</code></li>
	<li><code>1 &lt;=&nbsp;groupSizes[i] &lt;= n</code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def groupThePeople(self, groupSizes: List[int]) -> List[List[int]]:
        g = defaultdict(list)
        for i, v in enumerate(groupSizes):
            g[v].append(i)
        return [v[j : j + i] for i, v in g.items() for j in range(0, len(v), i)]
```

```java
class Solution {
    public List<List<Integer>> groupThePeople(int[] groupSizes) {
        int n = groupSizes.length;
        List<Integer>[] g = new List[n + 1];
        Arrays.setAll(g, k -> new ArrayList<>());
        for (int i = 0; i < n; ++i) {
            g[groupSizes[i]].add(i);
        }
        List<List<Integer>> ans = new ArrayList<>();
        for (int i = 0; i < g.length; ++i) {
            List<Integer> v = g[i];
            for (int j = 0; j < v.size(); j += i) {
                ans.add(v.subList(j, j + i));
            }
        }
        return ans;
    }
}
```

```cpp
class Solution {
public:
    vector<vector<int>> groupThePeople(vector<int>& groupSizes) {
        int n = groupSizes.size();
        vector<vector<int>> g(n + 1);
        for (int i = 0; i < n; ++i) g[groupSizes[i]].push_back(i);
        vector<vector<int>> ans;
        for (int i = 0; i < g.size(); ++i) {
            for (int j = 0; j < g[i].size(); j += i) {
                vector<int> t(g[i].begin() + j, g[i].begin() + j + i);
                ans.push_back(t);
            }
        }
        return ans;
    }
};
```

```go
func groupThePeople(groupSizes []int) [][]int {
	n := len(groupSizes)
	g := make([][]int, n+1)
	for i, v := range groupSizes {
		g[v] = append(g[v], i)
	}
	ans := [][]int{}
	for i, v := range g {
		for j := 0; j < len(v); j += i {
			ans = append(ans, v[j:j+i])
		}
	}
	return ans
}
```

```ts
function groupThePeople(groupSizes: number[]): number[][] {
    const res = [];
    const map = new Map<number, number[]>();
    const n = groupSizes.length;
    for (let i = 0; i < n; i++) {
        const size = groupSizes[i];
        map.set(size, [...(map.get(size) ?? []), i]);
        const arr = map.get(size);
        if (arr.length === size) {
            res.push(arr);
            map.set(size, []);
        }
    }
    return res;
}
```

```rust
use std::collections::HashMap;
impl Solution {
    pub fn group_the_people(group_sizes: Vec<i32>) -> Vec<Vec<i32>> {
        let mut res = vec![];
        let mut map = HashMap::new();
        for i in 0..group_sizes.len() {
            let size = group_sizes[i] as usize;
            let arr = map.entry(size).or_insert(vec![]);
            arr.push(i as i32);
            if arr.len() == size {
                res.push(arr.clone());
                arr.clear();
            }
        }
        res
    }
}
```

<!-- tabs:end -->

### Solution 2

<!-- tabs:start -->

```python
class Solution:
    def groupThePeople(self, groupSizes: List[int]) -> List[List[int]]:
        g = defaultdict(list)
        for i, x in enumerate(groupSizes):
            g[x].append(i)
        ans = []
        for x, idx in g.items():
            t = []
            for i in idx:
                t.append(i)
                if len(t) == x:
                    ans.append(t)
                    t = []
        return ans
```

```rust
impl Solution {
    #[allow(dead_code)]
    pub fn group_the_people(group_sizes: Vec<i32>) -> Vec<Vec<i32>> {
        let n = group_sizes.len();
        let mut g = vec![vec![]; n + 1];
        let mut ret = vec![];

        for i in 0..n {
            g[group_sizes[i] as usize].push(i as i32);
            if g[group_sizes[i] as usize].len() == (group_sizes[i] as usize) {
                ret.push(g[group_sizes[i] as usize].clone());
                g[group_sizes[i] as usize].clear();
            }
        }

        ret
    }
}
```

<!-- tabs:end -->

<!-- end -->
