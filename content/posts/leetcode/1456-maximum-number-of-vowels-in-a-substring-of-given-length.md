---
title: 1456 Maximum Number of Vowels in a Substring of Given Length
summary: 1456 Maximum Number of Vowels in a Substring of Given Length LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["1456 Maximum Number of Vowels in a Substring of Given Length LeetCode Solution Explained in all languages", "1456 Maximum Number of Vowels in a Substring of Given Length", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1456 Maximum Number of Vowels in a Substring of Given Length - Solution Explained/problem-solving.webp
    alt: 1456 Maximum Number of Vowels in a Substring of Given Length
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1456. Maximum Number of Vowels in a Substring of Given Length](https://leetcode.com/problems/maximum-number-of-vowels-in-a-substring-of-given-length)


## Description

<p>Given a string <code>s</code> and an integer <code>k</code>, return <em>the maximum number of vowel letters in any substring of </em><code>s</code><em> with length </em><code>k</code>.</p>

<p><strong>Vowel letters</strong> in English are <code>&#39;a&#39;</code>, <code>&#39;e&#39;</code>, <code>&#39;i&#39;</code>, <code>&#39;o&#39;</code>, and <code>&#39;u&#39;</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;abciiidef&quot;, k = 3
<strong>Output:</strong> 3
<strong>Explanation:</strong> The substring &quot;iii&quot; contains 3 vowel letters.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;aeiou&quot;, k = 2
<strong>Output:</strong> 2
<strong>Explanation:</strong> Any substring of length 2 contains 2 vowels.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;leetcode&quot;, k = 3
<strong>Output:</strong> 2
<strong>Explanation:</strong> &quot;lee&quot;, &quot;eet&quot; and &quot;ode&quot; contain 2 vowels.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>5</sup></code></li>
	<li><code>s</code> consists of lowercase English letters.</li>
	<li><code>1 &lt;= k &lt;= s.length</code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def maxVowels(self, s: str, k: int) -> int:
        vowels = set('aeiou')
        t = sum(c in vowels for c in s[:k])
        ans = t
        for i in range(k, len(s)):
            t += s[i] in vowels
            t -= s[i - k] in vowels
            ans = max(ans, t)
        return ans
```

```java
class Solution {
    public int maxVowels(String s, int k) {
        int t = 0, n = s.length();
        for (int i = 0; i < k; ++i) {
            if (isVowel(s.charAt(i))) {
                ++t;
            }
        }
        int ans = t;
        for (int i = k; i < n; ++i) {
            if (isVowel(s.charAt(i))) {
                ++t;
            }
            if (isVowel(s.charAt(i - k))) {
                --t;
            }
            ans = Math.max(ans, t);
        }
        return ans;
    }

    private boolean isVowel(char c) {
        return c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u';
    }
}
```

```cpp
class Solution {
public:
    int maxVowels(string s, int k) {
        int t = 0, n = s.size();
        for (int i = 0; i < k; ++i) t += isVowel(s[i]);
        int ans = t;
        for (int i = k; i < n; ++i) {
            t += isVowel(s[i]);
            t -= isVowel(s[i - k]);
            ans = max(ans, t);
        }
        return ans;
    }

    bool isVowel(char c) {
        return c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u';
    }
};
```

```go
func maxVowels(s string, k int) int {
	isVowel := func(c byte) bool {
		return c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u'
	}
	t := 0
	for i := 0; i < k; i++ {
		if isVowel(s[i]) {
			t++
		}
	}
	ans := t
	for i := k; i < len(s); i++ {
		if isVowel(s[i]) {
			t++
		}
		if isVowel(s[i-k]) {
			t--
		}
		ans = max(ans, t)
	}
	return ans
}
```

```ts
function maxVowels(s: string, k: number): number {
    function isVowel(c) {
        return c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u';
    }
    let t = 0;
    for (let i = 0; i < k; ++i) {
        if (isVowel(s.charAt(i))) {
            t++;
        }
    }
    let ans = t;
    for (let i = k; i < s.length; ++i) {
        if (isVowel(s.charAt(i))) {
            t++;
        }
        if (isVowel(s.charAt(i - k))) {
            t--;
        }
        ans = Math.max(ans, t);
    }
    return ans;
}
```

```php
class Solution {
    /**
     * @param String $s
     * @param Integer $k
     * @return Integer
     */
    function isVowel($c) {
        return $c === 'a' || $c === 'e' || $c === 'i' || $c === 'o' || $c === 'u';
    }
    function maxVowels($s, $k) {
        $cnt = 0;
        $rs = 0;
        for ($i = 0; $i < $k; $i++) {
            if ($this->isVowel($s[$i])) {
                $cnt++;
            }
        }
        $rs = $cnt;
        for ($j = $k; $j < strlen($s); $j++) {
            if ($this->isVowel($s[$j - $k])) {
                $cnt--;
            }
            if ($this->isVowel($s[$j])) {
                $cnt++;
            }
            $rs = max($rs, $cnt);
        }
        return $rs;
    }
}
```

<!-- tabs:end -->

<!-- end -->
