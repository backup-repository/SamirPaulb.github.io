---
title: 0686 Repeated String Match
summary: 0686 Repeated String Match LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["0686 Repeated String Match LeetCode Solution Explained in all languages", "0686 Repeated String Match", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0686 Repeated String Match - Solution Explained/problem-solving.webp
    alt: 0686 Repeated String Match
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [686. Repeated String Match](https://leetcode.com/problems/repeated-string-match)


## Description

<p>Given two strings <code>a</code> and <code>b</code>, return <em>the minimum number of times you should repeat string </em><code>a</code><em> so that string</em> <code>b</code> <em>is a substring of it</em>. If it is impossible for <code>b</code>​​​​​​ to be a substring of <code>a</code> after repeating it, return <code>-1</code>.</p>

<p><strong>Notice:</strong> string <code>&quot;abc&quot;</code> repeated 0 times is <code>&quot;&quot;</code>, repeated 1 time is <code>&quot;abc&quot;</code> and repeated 2 times is <code>&quot;abcabc&quot;</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> a = &quot;abcd&quot;, b = &quot;cdabcdab&quot;
<strong>Output:</strong> 3
<strong>Explanation:</strong> We return 3 because by repeating a three times &quot;ab<strong>cdabcdab</strong>cd&quot;, b is a substring of it.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> a = &quot;a&quot;, b = &quot;aa&quot;
<strong>Output:</strong> 2
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= a.length, b.length &lt;= 10<sup>4</sup></code></li>
	<li><code>a</code> and <code>b</code> consist of lowercase English letters.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def repeatedStringMatch(self, a: str, b: str) -> int:
        m, n = len(a), len(b)
        ans = ceil(n / m)
        t = [a] * ans
        for _ in range(3):
            if b in ''.join(t):
                return ans
            ans += 1
            t.append(a)
        return -1
```

```java
class Solution {
    public int repeatedStringMatch(String a, String b) {
        int m = a.length(), n = b.length();
        int ans = (n + m - 1) / m;
        StringBuilder t = new StringBuilder(a.repeat(ans));
        for (int i = 0; i < 3; ++i) {
            if (t.toString().contains(b)) {
                return ans;
            }
            ++ans;
            t.append(a);
        }
        return -1;
    }
}
```

```cpp
class Solution {
public:
    int repeatedStringMatch(string a, string b) {
        int m = a.size(), n = b.size();
        int ans = (n + m - 1) / m;
        string t = "";
        for (int i = 0; i < ans; ++i) t += a;
        for (int i = 0; i < 3; ++i) {
            if (t.find(b) != -1) return ans;
            ++ans;
            t += a;
        }
        return -1;
    }
};
```

```go
func repeatedStringMatch(a string, b string) int {
	m, n := len(a), len(b)
	ans := (n + m - 1) / m
	t := strings.Repeat(a, ans)
	for i := 0; i < 3; i++ {
		if strings.Contains(t, b) {
			return ans
		}
		ans++
		t += a
	}
	return -1
}
```

```ts
function repeatedStringMatch(a: string, b: string): number {
    const m: number = a.length,
        n: number = b.length;
    let ans: number = Math.ceil(n / m);
    let t: string = a.repeat(ans);

    for (let i = 0; i < 3; i++) {
        if (t.includes(b)) {
            return ans;
        }
        ans++;
        t += a;
    }

    return -1;
}
```

<!-- tabs:end -->

<!-- end -->
