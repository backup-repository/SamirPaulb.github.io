---
title: 2178 Maximum Split of Positive Even Integers
summary: 2178 Maximum Split of Positive Even Integers LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["2178 Maximum Split of Positive Even Integers LeetCode Solution Explained in all languages", "2178 Maximum Split of Positive Even Integers", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:2178 Maximum Split of Positive Even Integers - Solution Explained/problem-solving.webp
    alt: 2178 Maximum Split of Positive Even Integers
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [2178. Maximum Split of Positive Even Integers](https://leetcode.com/problems/maximum-split-of-positive-even-integers)


## Description

<p>You are given an integer <code>finalSum</code>. Split it into a sum of a <strong>maximum</strong> number of <strong>unique</strong> positive even integers.</p>

<ul>
	<li>For example, given <code>finalSum = 12</code>, the following splits are <strong>valid</strong> (unique positive even integers summing up to <code>finalSum</code>): <code>(12)</code>, <code>(2 + 10)</code>, <code>(2 + 4 + 6)</code>, and <code>(4 + 8)</code>. Among them, <code>(2 + 4 + 6)</code> contains the maximum number of integers. Note that <code>finalSum</code> cannot be split into <code>(2 + 2 + 4 + 4)</code> as all the numbers should be unique.</li>
</ul>

<p>Return <em>a list of integers that represent a valid split containing a <strong>maximum</strong> number of integers</em>. If no valid split exists for <code>finalSum</code>, return <em>an <strong>empty</strong> list</em>. You may return the integers in <strong>any</strong> order.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> finalSum = 12
<strong>Output:</strong> [2,4,6]
<strong>Explanation:</strong> The following are valid splits: <code>(12)</code>, <code>(2 + 10)</code>, <code>(2 + 4 + 6)</code>, and <code>(4 + 8)</code>.
(2 + 4 + 6) has the maximum number of integers, which is 3. Thus, we return [2,4,6].
Note that [2,6,4], [6,2,4], etc. are also accepted.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> finalSum = 7
<strong>Output:</strong> []
<strong>Explanation:</strong> There are no valid splits for the given finalSum.
Thus, we return an empty array.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> finalSum = 28
<strong>Output:</strong> [6,8,2,12]
<strong>Explanation:</strong> The following are valid splits: <code>(2 + 26)</code>, <code>(6 + 8 + 2 + 12)</code>, and <code>(4 + 24)</code>. 
<code>(6 + 8 + 2 + 12)</code> has the maximum number of integers, which is 4. Thus, we return [6,8,2,12].
Note that [10,2,4,12], [6,2,4,16], etc. are also accepted.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= finalSum &lt;= 10<sup>10</sup></code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def maximumEvenSplit(self, finalSum: int) -> List[int]:
        if finalSum % 2:
            return []
        i = 2
        ans = []
        while i <= finalSum:
            ans.append(i)
            finalSum -= i
            i += 2
        ans[-1] += finalSum
        return ans
```

```java
class Solution {
    public List<Long> maximumEvenSplit(long finalSum) {
        List<Long> ans = new ArrayList<>();
        if (finalSum % 2 == 1) {
            return ans;
        }
        for (long i = 2; i <= finalSum; i += 2) {
            ans.add(i);
            finalSum -= i;
        }
        ans.add(ans.remove(ans.size() - 1) + finalSum);
        return ans;
    }
}
```

```cpp
class Solution {
public:
    vector<long long> maximumEvenSplit(long long finalSum) {
        vector<long long> ans;
        if (finalSum % 2) return ans;
        for (long long i = 2; i <= finalSum; i += 2) {
            ans.push_back(i);
            finalSum -= i;
        }
        ans.back() += finalSum;
        return ans;
    }
};
```

```go
func maximumEvenSplit(finalSum int64) (ans []int64) {
	if finalSum%2 == 1 {
		return
	}
	for i := int64(2); i <= finalSum; i += 2 {
		ans = append(ans, i)
		finalSum -= i
	}
	ans[len(ans)-1] += finalSum
	return
}
```

```ts
function maximumEvenSplit(finalSum: number): number[] {
    const ans: number[] = [];
    if (finalSum % 2 === 1) {
        return ans;
    }
    for (let i = 2; i <= finalSum; i += 2) {
        ans.push(i);
        finalSum -= i;
    }
    ans[ans.length - 1] += finalSum;
    return ans;
}
```

```cs
public class Solution {
    public IList<long> MaximumEvenSplit(long finalSum) {
        IList<long> ans = new List<long>();
        if (finalSum % 2 == 1) {
            return ans;
        }
        for (long i = 2; i <= finalSum; i += 2) {
            ans.Add(i);
            finalSum -= i;
        }
        ans[ans.Count - 1] += finalSum;
        return ans;
    }
}
```

<!-- tabs:end -->

<!-- end -->
