---
title: 0564 Find the Closest Palindrome
summary: 0564 Find the Closest Palindrome LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["0564 Find the Closest Palindrome LeetCode Solution Explained in all languages", "0564 Find the Closest Palindrome", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0564 Find the Closest Palindrome - Solution Explained/problem-solving.webp
    alt: 0564 Find the Closest Palindrome
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [564. Find the Closest Palindrome](https://leetcode.com/problems/find-the-closest-palindrome)


## Description

<p>Given a string <code>n</code> representing an integer, return <em>the closest integer (not including itself), which is a palindrome</em>. If there is a tie, return <em><strong>the smaller one</strong></em>.</p>

<p>The closest is defined as the absolute difference minimized between two integers.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> n = &quot;123&quot;
<strong>Output:</strong> &quot;121&quot;
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = &quot;1&quot;
<strong>Output:</strong> &quot;0&quot;
<strong>Explanation:</strong> 0 and 2 are the closest palindromes but we return the smallest which is 0.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n.length &lt;= 18</code></li>
	<li><code>n</code> consists of only digits.</li>
	<li><code>n</code> does not have leading zeros.</li>
	<li><code>n</code> is representing an integer in the range <code>[1, 10<sup>18</sup> - 1]</code>.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def nearestPalindromic(self, n: str) -> str:
        x = int(n)
        l = len(n)
        res = {10 ** (l - 1) - 1, 10**l + 1}
        left = int(n[: (l + 1) >> 1])
        for i in range(left - 1, left + 2):
            j = i if l % 2 == 0 else i // 10
            while j:
                i = i * 10 + j % 10
                j //= 10
            res.add(i)
        res.discard(x)

        ans = -1
        for t in res:
            if (
                ans == -1
                or abs(t - x) < abs(ans - x)
                or (abs(t - x) == abs(ans - x) and t < ans)
            ):
                ans = t
        return str(ans)
```

```java
class Solution {
    public String nearestPalindromic(String n) {
        long x = Long.parseLong(n);
        long ans = -1;
        for (long t : get(n)) {
            if (ans == -1 || Math.abs(t - x) < Math.abs(ans - x)
                || (Math.abs(t - x) == Math.abs(ans - x) && t < ans)) {
                ans = t;
            }
        }
        return Long.toString(ans);
    }

    private Set<Long> get(String n) {
        int l = n.length();
        Set<Long> res = new HashSet<>();
        res.add((long) Math.pow(10, l - 1) - 1);
        res.add((long) Math.pow(10, l) + 1);
        long left = Long.parseLong(n.substring(0, (l + 1) / 2));
        for (long i = left - 1; i <= left + 1; ++i) {
            StringBuilder sb = new StringBuilder();
            sb.append(i);
            sb.append(new StringBuilder(i + "").reverse().substring(l & 1));
            res.add(Long.parseLong(sb.toString()));
        }
        res.remove(Long.parseLong(n));
        return res;
    }
}
```

```cpp
class Solution {
public:
    string nearestPalindromic(string n) {
        long x = stol(n);
        long ans = -1;
        for (long t : get(n))
            if (ans == -1 || abs(t - x) < abs(ans - x) || (abs(t - x) == abs(ans - x) && t < ans))
                ans = t;
        return to_string(ans);
    }

    unordered_set<long> get(string& n) {
        int l = n.size();
        unordered_set<long> res;
        res.insert((long) pow(10, l - 1) - 1);
        res.insert((long) pow(10, l) + 1);
        long left = stol(n.substr(0, (l + 1) / 2));
        for (long i = left - 1; i <= left + 1; ++i) {
            string prefix = to_string(i);
            string t = prefix + string(prefix.rbegin() + (l & 1), prefix.rend());
            res.insert(stol(t));
        }
        res.erase(stol(n));
        return res;
    }
};
```

```go
func nearestPalindromic(n string) string {
	l := len(n)
	res := []int{int(math.Pow10(l-1)) - 1, int(math.Pow10(l)) + 1}
	left, _ := strconv.Atoi(n[:(l+1)/2])
	for _, x := range []int{left - 1, left, left + 1} {
		y := x
		if l&1 == 1 {
			y /= 10
		}
		for ; y > 0; y /= 10 {
			x = x*10 + y%10
		}
		res = append(res, x)
	}
	ans := -1
	x, _ := strconv.Atoi(n)
	for _, t := range res {
		if t != x {
			if ans == -1 || abs(t-x) < abs(ans-x) || abs(t-x) == abs(ans-x) && t < ans {
				ans = t
			}
		}
	}
	return strconv.Itoa(ans)
}

func abs(x int) int {
	if x < 0 {
		return -x
	}
	return x
}
```

<!-- tabs:end -->

<!-- end -->
