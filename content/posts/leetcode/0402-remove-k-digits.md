---
title: 0402 Remove K Digits
summary: 0402 Remove K Digits LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["0402 Remove K Digits LeetCode Solution Explained in all languages", "0402 Remove K Digits", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0402 Remove K Digits - Solution Explained/problem-solving.webp
    alt: 0402 Remove K Digits
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [402. Remove K Digits](https://leetcode.com/problems/remove-k-digits)


## Description

<p>Given string num representing a non-negative integer <code>num</code>, and an integer <code>k</code>, return <em>the smallest possible integer after removing</em> <code>k</code> <em>digits from</em> <code>num</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> num = &quot;1432219&quot;, k = 3
<strong>Output:</strong> &quot;1219&quot;
<strong>Explanation:</strong> Remove the three digits 4, 3, and 2 to form the new number 1219 which is the smallest.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> num = &quot;10200&quot;, k = 1
<strong>Output:</strong> &quot;200&quot;
<strong>Explanation:</strong> Remove the leading 1 and the number is 200. Note that the output must not contain leading zeroes.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> num = &quot;10&quot;, k = 2
<strong>Output:</strong> &quot;0&quot;
<strong>Explanation:</strong> Remove all the digits from the number and it is left with nothing which is 0.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= k &lt;= num.length &lt;= 10<sup>5</sup></code></li>
	<li><code>num</code> consists of only digits.</li>
	<li><code>num</code> does not have any leading zeros except for the zero itself.</li>
</ul>

## Solutions

### Solution 1: Greedy Algorithm

<!-- tabs:start -->

```python
class Solution:
    def removeKdigits(self, num: str, k: int) -> str:
        stk = []
        remain = len(num) - k
        for c in num:
            while k and stk and stk[-1] > c:
                stk.pop()
                k -= 1
            stk.append(c)
        return ''.join(stk[:remain]).lstrip('0') or '0'
```

```java
class Solution {
    public String removeKdigits(String num, int k) {
        StringBuilder stk = new StringBuilder();
        for (char c : num.toCharArray()) {
            while (k > 0 && stk.length() > 0 && stk.charAt(stk.length() - 1) > c) {
                stk.deleteCharAt(stk.length() - 1);
                --k;
            }
            stk.append(c);
        }
        for (; k > 0; --k) {
            stk.deleteCharAt(stk.length() - 1);
        }
        int i = 0;
        for (; i < stk.length() && stk.charAt(i) == '0'; ++i) {
        }
        String ans = stk.substring(i);
        return "".equals(ans) ? "0" : ans;
    }
}
```

```cpp
class Solution {
public:
    string removeKdigits(string num, int k) {
        string stk;
        for (char& c : num) {
            while (k && stk.size() && stk.back() > c) {
                stk.pop_back();
                --k;
            }
            stk += c;
        }
        while (k--) {
            stk.pop_back();
        }
        int i = 0;
        for (; i < stk.size() && stk[i] == '0'; ++i) {
        }
        string ans = stk.substr(i);
        return ans == "" ? "0" : ans;
    }
};
```

```go
func removeKdigits(num string, k int) string {
	stk, remain := make([]byte, 0), len(num)-k
	for i := 0; i < len(num); i++ {
		n := len(stk)
		for k > 0 && n > 0 && stk[n-1] > num[i] {
			stk = stk[:n-1]
			n, k = n-1, k-1
		}
		stk = append(stk, num[i])
	}

	for i := 0; i < len(stk) && i < remain; i++ {
		if stk[i] != '0' {
			return string(stk[i:remain])
		}
	}
	return "0"
}
```

```ts
function removeKdigits(num: string, k: number): string {
    let nums = [...num];
    while (k > 0) {
        let idx = 0;
        while (idx < nums.length - 1 && nums[idx + 1] >= nums[idx]) {
            idx++;
        }
        nums.splice(idx, 1);
        k--;
    }
    return nums.join('').replace(/^0*/g, '') || '0';
}
```

<!-- tabs:end -->

<!-- end -->
