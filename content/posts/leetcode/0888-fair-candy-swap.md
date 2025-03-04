---
title: 0888 Fair Candy Swap
summary: 0888 Fair Candy Swap LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["0888 Fair Candy Swap LeetCode Solution Explained in all languages", "0888 Fair Candy Swap", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0888 Fair Candy Swap - Solution Explained/problem-solving.webp
    alt: 0888 Fair Candy Swap
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [888. Fair Candy Swap](https://leetcode.com/problems/fair-candy-swap)


## Description

<p>Alice and Bob have a different total number of candies. You are given two integer arrays <code>aliceSizes</code> and <code>bobSizes</code> where <code>aliceSizes[i]</code> is the number of candies of the <code>i<sup>th</sup></code> box of candy that Alice has and <code>bobSizes[j]</code> is the number of candies of the <code>j<sup>th</sup></code> box of candy that Bob has.</p>

<p>Since they are friends, they would like to exchange one candy box each so that after the exchange, they both have the same total amount of candy. The total amount of candy a person has is the sum of the number of candies in each box they have.</p>

<p>Return a<em>n integer array </em><code>answer</code><em> where </em><code>answer[0]</code><em> is the number of candies in the box that Alice must exchange, and </em><code>answer[1]</code><em> is the number of candies in the box that Bob must exchange</em>. If there are multiple answers, you may <strong>return any</strong> one of them. It is guaranteed that at least one answer exists.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> aliceSizes = [1,1], bobSizes = [2,2]
<strong>Output:</strong> [1,2]
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> aliceSizes = [1,2], bobSizes = [2,3]
<strong>Output:</strong> [1,2]
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> aliceSizes = [2], bobSizes = [1,3]
<strong>Output:</strong> [2,3]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= aliceSizes.length, bobSizes.length &lt;= 10<sup>4</sup></code></li>
	<li><code>1 &lt;= aliceSizes[i], bobSizes[j] &lt;= 10<sup>5</sup></code></li>
	<li>Alice and Bob have a different total number of candies.</li>
	<li>There will be at least one valid answer for the given input.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def fairCandySwap(self, aliceSizes: List[int], bobSizes: List[int]) -> List[int]:
        diff = (sum(aliceSizes) - sum(bobSizes)) >> 1
        s = set(bobSizes)
        for a in aliceSizes:
            target = a - diff
            if target in s:
                return [a, target]
```

```java
class Solution {
    public int[] fairCandySwap(int[] aliceSizes, int[] bobSizes) {
        int s1 = 0, s2 = 0;
        Set<Integer> s = new HashSet<>();
        for (int a : aliceSizes) {
            s1 += a;
        }
        for (int b : bobSizes) {
            s.add(b);
            s2 += b;
        }
        int diff = (s1 - s2) >> 1;
        for (int a : aliceSizes) {
            int target = a - diff;
            if (s.contains(target)) {
                return new int[] {a, target};
            }
        }
        return null;
    }
}
```

```cpp
class Solution {
public:
    vector<int> fairCandySwap(vector<int>& aliceSizes, vector<int>& bobSizes) {
        int s1 = accumulate(aliceSizes.begin(), aliceSizes.end(), 0);
        int s2 = accumulate(bobSizes.begin(), bobSizes.end(), 0);
        int diff = (s1 - s2) >> 1;
        unordered_set<int> s(bobSizes.begin(), bobSizes.end());
        vector<int> ans;
        for (int& a : aliceSizes) {
            int target = a - diff;
            if (s.count(target)) {
                ans = vector<int>{a, target};
                break;
            }
        }
        return ans;
    }
};
```

```ts
function fairCandySwap(aliceSizes: number[], bobSizes: number[]): number[] {
    let s1 = aliceSizes.reduce((a, c) => a + c, 0);
    let s2 = bobSizes.reduce((a, c) => a + c, 0);
    let diff = (s1 - s2) >> 1;
    for (let num of aliceSizes) {
        let target = num - diff;
        if (bobSizes.includes(target)) {
            return [num, target];
        }
    }
}
```

<!-- tabs:end -->

<!-- end -->
