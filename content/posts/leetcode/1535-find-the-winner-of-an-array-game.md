---
title: 1535 Find the Winner of an Array Game
summary: 1535 Find the Winner of an Array Game LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["1535 Find the Winner of an Array Game LeetCode Solution Explained in all languages", "1535 Find the Winner of an Array Game", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1535 Find the Winner of an Array Game - Solution Explained/problem-solving.webp
    alt: 1535 Find the Winner of an Array Game
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1535. Find the Winner of an Array Game](https://leetcode.com/problems/find-the-winner-of-an-array-game)


## Description

<p>Given an integer array <code>arr</code> of <strong>distinct</strong> integers and an integer <code>k</code>.</p>

<p>A game will be played between the first two elements of the array (i.e. <code>arr[0]</code> and <code>arr[1]</code>). In each round of the game, we compare <code>arr[0]</code> with <code>arr[1]</code>, the larger integer wins and remains at position <code>0</code>, and the smaller integer moves to the end of the array. The game ends when an integer wins <code>k</code> consecutive rounds.</p>

<p>Return <em>the integer which will win the game</em>.</p>

<p>It is <strong>guaranteed</strong> that there will be a winner of the game.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> arr = [2,1,3,5,4,6,7], k = 2
<strong>Output:</strong> 5
<strong>Explanation:</strong> Let&#39;s see the rounds of the game:
Round |       arr       | winner | win_count
  1   | [2,1,3,5,4,6,7] | 2      | 1
  2   | [2,3,5,4,6,7,1] | 3      | 1
  3   | [3,5,4,6,7,1,2] | 5      | 1
  4   | [5,4,6,7,1,2,3] | 5      | 2
So we can see that 4 rounds will be played and 5 is the winner because it wins 2 consecutive games.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> arr = [3,2,1], k = 10
<strong>Output:</strong> 3
<strong>Explanation:</strong> 3 will win the first 10 rounds consecutively.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>2 &lt;= arr.length &lt;= 10<sup>5</sup></code></li>
	<li><code>1 &lt;= arr[i] &lt;= 10<sup>6</sup></code></li>
	<li><code>arr</code> contains <strong>distinct</strong> integers.</li>
	<li><code>1 &lt;= k &lt;= 10<sup>9</sup></code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def getWinner(self, arr: List[int], k: int) -> int:
        mx = arr[0]
        cnt = 0
        for x in arr[1:]:
            if mx < x:
                mx = x
                cnt = 1
            else:
                cnt += 1
            if cnt == k:
                break
        return mx
```

```java
class Solution {
    public int getWinner(int[] arr, int k) {
        int mx = arr[0];
        for (int i = 1, cnt = 0; i < arr.length; ++i) {
            if (mx < arr[i]) {
                mx = arr[i];
                cnt = 1;
            } else {
                ++cnt;
            }
            if (cnt == k) {
                break;
            }
        }
        return mx;
    }
}
```

```cpp
class Solution {
public:
    int getWinner(vector<int>& arr, int k) {
        int mx = arr[0];
        for (int i = 1, cnt = 0; i < arr.size(); ++i) {
            if (mx < arr[i]) {
                mx = arr[i];
                cnt = 1;
            } else {
                ++cnt;
            }
            if (cnt == k) {
                break;
            }
        }
        return mx;
    }
};
```

```go
func getWinner(arr []int, k int) int {
	mx, cnt := arr[0], 0
	for _, x := range arr[1:] {
		if mx < x {
			mx = x
			cnt = 1
		} else {
			cnt++
		}
		if cnt == k {
			break
		}
	}
	return mx
}
```

```ts
function getWinner(arr: number[], k: number): number {
    let mx = arr[0];
    let cnt = 0;
    for (const x of arr.slice(1)) {
        if (mx < x) {
            mx = x;
            cnt = 1;
        } else {
            ++cnt;
        }
        if (cnt === k) {
            break;
        }
    }
    return mx;
}
```

```cs
public class Solution {
    public int GetWinner(int[] arr, int k) {
        int maxElement = arr[0], count = 0;
        for (int i = 1; i < arr.Length; i++) {
            if (maxElement < arr[i]) {
                maxElement = arr[i];
                count = 1;
            } else {
                count++;
            }
            if (count == k) {
                break;
            }
        }
        return maxElement;
    }
}
```

<!-- tabs:end -->

<!-- end -->
