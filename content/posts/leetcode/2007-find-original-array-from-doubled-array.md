---
title: 2007 Find Original Array From Doubled Array
summary: 2007 Find Original Array From Doubled Array LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["2007 Find Original Array From Doubled Array LeetCode Solution Explained in all languages", "2007 Find Original Array From Doubled Array", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:2007 Find Original Array From Doubled Array - Solution Explained/problem-solving.webp
    alt: 2007 Find Original Array From Doubled Array
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [2007. Find Original Array From Doubled Array](https://leetcode.com/problems/find-original-array-from-doubled-array)


## Description

<p>An integer array <code>original</code> is transformed into a <strong>doubled</strong> array <code>changed</code> by appending <strong>twice the value</strong> of every element in <code>original</code>, and then randomly <strong>shuffling</strong> the resulting array.</p>

<p>Given an array <code>changed</code>, return <code>original</code><em> if </em><code>changed</code><em> is a <strong>doubled</strong> array. If </em><code>changed</code><em> is not a <strong>doubled</strong> array, return an empty array. The elements in</em> <code>original</code> <em>may be returned in <strong>any</strong> order</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> changed = [1,3,4,2,6,8]
<strong>Output:</strong> [1,3,4]
<strong>Explanation:</strong> One possible original array could be [1,3,4]:
- Twice the value of 1 is 1 * 2 = 2.
- Twice the value of 3 is 3 * 2 = 6.
- Twice the value of 4 is 4 * 2 = 8.
Other original arrays could be [4,3,1] or [3,1,4].
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> changed = [6,3,0,1]
<strong>Output:</strong> []
<strong>Explanation:</strong> changed is not a doubled array.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> changed = [1]
<strong>Output:</strong> []
<strong>Explanation:</strong> changed is not a doubled array.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= changed.length &lt;= 10<sup>5</sup></code></li>
	<li><code>0 &lt;= changed[i] &lt;= 10<sup>5</sup></code></li>
</ul>

## Solutions

### Solution 1: Sorting + Counting + Traversal

First, we check if the length $n$ of the array `changed` is odd. If it is, we directly return an empty array.

Then, we sort the array `changed`, and use a hash table or array `cnt` to count the occurrence of each element in `changed`.

Next, we traverse the array `changed`. For each element $x$ in `changed`, we first check if $x$ exists in the hash table `cnt`. If it does not exist, we directly skip this element. Otherwise, we check if $x \times 2$ exists in `cnt`. If it does not exist, we directly return an empty array. Otherwise, we add $x$ to the answer array `ans`, and decrease the occurrence counts of $x$ and $x \times 2$ in `cnt` by $1$ each.

After the traversal, we check if the length of the answer array `ans` is $\frac{n}{2}$. If it is, we return `ans`, otherwise we return an empty array.

The time complexity is $O(n \times \log n)$, and the space complexity is $O(n)$. Here, $n$ is the length of the array `changed`.

<!-- tabs:start -->

```python
class Solution:
    def findOriginalArray(self, changed: List[int]) -> List[int]:
        n = len(changed)
        if n & 1:
            return []
        cnt = Counter(changed)
        changed.sort()
        ans = []
        for x in changed:
            if cnt[x] == 0:
                continue
            if cnt[x * 2] <= 0:
                return []
            ans.append(x)
            cnt[x] -= 1
            cnt[x * 2] -= 1
        return ans if len(ans) == n // 2 else []
```

```java
class Solution {
    public int[] findOriginalArray(int[] changed) {
        int n = changed.length;
        if (n % 2 == 1) {
            return new int[] {};
        }
        Arrays.sort(changed);
        int[] cnt = new int[changed[n - 1] + 1];
        for (int x : changed) {
            ++cnt[x];
        }
        int[] ans = new int[n / 2];
        int i = 0;
        for (int x : changed) {
            if (cnt[x] == 0) {
                continue;
            }
            if (x * 2 >= cnt.length || cnt[x * 2] <= 0) {
                return new int[] {};
            }
            ans[i++] = x;
            cnt[x]--;
            cnt[x * 2]--;
        }
        return i == n / 2 ? ans : new int[] {};
    }
}
```

```cpp
class Solution {
public:
    vector<int> findOriginalArray(vector<int>& changed) {
        int n = changed.size();
        if (n & 1) {
            return {};
        }
        sort(changed.begin(), changed.end());
        vector<int> cnt(changed.back() + 1);
        for (int& x : changed) {
            ++cnt[x];
        }
        vector<int> ans;
        for (int& x : changed) {
            if (cnt[x] == 0) {
                continue;
            }
            if (x * 2 >= cnt.size() || cnt[x * 2] <= 0) {
                return {};
            }
            ans.push_back(x);
            --cnt[x];
            --cnt[x * 2];
        }
        return ans.size() == n / 2 ? ans : vector<int>();
    }
};
```

```go
func findOriginalArray(changed []int) []int {
	n := len(changed)
	ans := []int{}
	if n&1 == 1 {
		return ans
	}
	sort.Ints(changed)
	cnt := make([]int, changed[n-1]+1)
	for _, x := range changed {
		cnt[x]++
	}
	for _, x := range changed {
		if cnt[x] == 0 {
			continue
		}
		if x*2 >= len(cnt) || cnt[x*2] <= 0 {
			return []int{}
		}
		ans = append(ans, x)
		cnt[x]--
		cnt[x*2]--
	}
	if len(ans) != n/2 {
		return []int{}
	}
	return ans
}
```

```ts
function findOriginalArray(changed: number[]): number[] {
    const n = changed.length;
    if (n & 1) {
        return [];
    }
    const cnt = new Map<number, number>();
    for (const x of changed) {
        cnt.set(x, (cnt.get(x) || 0) + 1);
    }
    changed.sort((a, b) => a - b);
    const ans: number[] = [];
    for (const x of changed) {
        if (cnt.get(x) == 0) {
            continue;
        }
        if ((cnt.get(x * 2) || 0) <= 0) {
            return [];
        }
        ans.push(x);
        cnt.set(x, (cnt.get(x) || 0) - 1);
        cnt.set(x * 2, (cnt.get(x * 2) || 0) - 1);
    }
    return ans.length == n / 2 ? ans : [];
}
```

<!-- tabs:end -->

<!-- end -->
