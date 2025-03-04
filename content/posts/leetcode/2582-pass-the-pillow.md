---
title: 2582 Pass the Pillow
summary: 2582 Pass the Pillow LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["2582 Pass the Pillow LeetCode Solution Explained in all languages", "2582 Pass the Pillow", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:2582 Pass the Pillow - Solution Explained/problem-solving.webp
    alt: 2582 Pass the Pillow
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [2582. Pass the Pillow](https://leetcode.com/problems/pass-the-pillow)


## Description

<p>There are <code>n</code> people standing in a line labeled from <code>1</code> to <code>n</code>. The first person in the line is holding a pillow initially. Every second, the person holding the pillow passes it to the next person standing in the line. Once the pillow reaches the end of the line, the direction changes, and people continue passing the pillow in the opposite direction.</p>

<ul>
	<li>For example, once the pillow reaches the <code>n<sup>th</sup></code> person they pass it to the <code>n - 1<sup>th</sup></code> person, then to the <code>n - 2<sup>th</sup></code> person and so on.</li>
</ul>

<p>Given the two positive integers <code>n</code> and <code>time</code>, return <em>the index of the person holding the pillow after </em><code>time</code><em> seconds</em>.</p>
<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> n = 4, time = 5
<strong>Output:</strong> 2
<strong>Explanation:</strong> People pass the pillow in the following way: 1 -&gt; 2 -&gt; 3 -&gt; 4 -&gt; 3 -&gt; 2.
Afer five seconds, the pillow is given to the 2<sup>nd</sup> person.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = 3, time = 2
<strong>Output:</strong> 3
<strong>Explanation:</strong> People pass the pillow in the following way: 1 -&gt; 2 -&gt; 3.
Afer two seconds, the pillow is given to the 3<sup>r</sup><sup>d</sup> person.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>2 &lt;= n &lt;= 1000</code></li>
	<li><code>1 &lt;= time &lt;= 1000</code></li>
</ul>

## Solutions

### Solution 1: Simulation

We can simulate the process of passing the pillow, and each time the pillow is passed, if the pillow reaches the front or the end of the queue, the direction of the pillow will change, and the queue will continue to pass the pillow along the opposite direction.

The time complexity is $O(time)$ and the space complexity is $O(1)$, where $time$ is the given time.

<!-- tabs:start -->

```python
class Solution:
    def passThePillow(self, n: int, time: int) -> int:
        ans = k = 1
        for _ in range(time):
            ans += k
            if ans == 1 or ans == n:
                k *= -1
        return ans
```

```java
class Solution {
    public int passThePillow(int n, int time) {
        int ans = 1, k = 1;
        while (time-- > 0) {
            ans += k;
            if (ans == 1 || ans == n) {
                k *= -1;
            }
        }
        return ans;
    }
}
```

```cpp
class Solution {
public:
    int passThePillow(int n, int time) {
        int ans = 1, k = 1;
        while (time--) {
            ans += k;
            if (ans == 1 || ans == n) {
                k *= -1;
            }
        }
        return ans;
    }
};
```

```go
func passThePillow(n int, time int) int {
	ans, k := 1, 1
	for ; time > 0; time-- {
		ans += k
		if ans == 1 || ans == n {
			k *= -1
		}
	}
	return ans
}
```

```ts
function passThePillow(n: number, time: number): number {
    let ans = 1,
        k = 1;
    while (time-- > 0) {
        ans += k;
        if (ans === 1 || ans === n) {
            k *= -1;
        }
    }
    return ans;
}
```

```rust
impl Solution {
    pub fn pass_the_pillow(n: i32, time: i32) -> i32 {
        let mut ans = 1;
        let mut k = 1;

        for i in 1..=time {
            ans += k;

            if ans == 1 || ans == n {
                k *= -1;
            }
        }

        ans
    }
}
```

<!-- tabs:end -->

### Solution 2: Math

We notice that there are $n - 1$ passes in each round. Therefore, we can divide $time$ by $n - 1$ to get the number of rounds $k$ that the pillow is passed, and then take the remainder of $time$ modulo $n - 1$ to get the remaining passes $mod$ in the current round.

Then we judge the current round $k$:

-   If $k$ is odd, then the current direction of the pillow is from the end of the queue to the front, so the pillow will be passed to the person with the number $n - mod$.
-   If $k$ is even, then the current direction of the pillow is from the front of the queue to the back, so the pillow will be passed to the person with the number $mod + 1$.

The time complexity is $O(1)$ and the space complexity is $O(1)$.

<!-- tabs:start -->

```python
class Solution:
    def passThePillow(self, n: int, time: int) -> int:
        k, mod = divmod(time, n - 1)
        return n - mod if k & 1 else mod + 1
```

```java
class Solution {
    public int passThePillow(int n, int time) {
        int k = time / (n - 1);
        int mod = time % (n - 1);
        return (k & 1) == 1 ? n - mod : mod + 1;
    }
}
```

```cpp
class Solution {
public:
    int passThePillow(int n, int time) {
        int k = time / (n - 1);
        int mod = time % (n - 1);
        return k & 1 ? n - mod : mod + 1;
    }
};
```

```go
func passThePillow(n int, time int) int {
	k, mod := time/(n-1), time%(n-1)
	if k&1 == 1 {
		return n - mod
	}
	return mod + 1
}
```

```ts
function passThePillow(n: number, time: number): number {
    const k = time / (n - 1);
    const mod = time % (n - 1);
    return (k & 1) == 1 ? n - mod : mod + 1;
}
```

```rust
impl Solution {
    pub fn pass_the_pillow(n: i32, time: i32) -> i32 {
        let mut k = time / (n - 1);
        let mut _mod = time % (n - 1);

        if (k & 1) == 1 {
            return n - _mod;
        }

        _mod + 1
    }
}
```

<!-- tabs:end -->

<!-- end -->
