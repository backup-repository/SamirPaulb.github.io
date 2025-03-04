---
title: 2618 Check if Object Instance of Class
summary: 2618 Check if Object Instance of Class LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["2618 Check if Object Instance of Class LeetCode Solution Explained in all languages", "2618 Check if Object Instance of Class", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:2618 Check if Object Instance of Class - Solution Explained/problem-solving.webp
    alt: 2618 Check if Object Instance of Class
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [2618. Check if Object Instance of Class](https://leetcode.com/problems/check-if-object-instance-of-class)


## Description

<p>Write a function that checks if a given value&nbsp;is an instance of a given class or superclass. For this problem, an object is considered an instance of a given class if that object has access to that class&#39;s methods.</p>

<p>There are&nbsp;no constraints on the data types that can be passed to the function. For example, the value or the class could be&nbsp;<code>undefined</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> func = () =&gt; checkIfInstanceOf(new Date(), Date)
<strong>Output:</strong> true
<strong>Explanation: </strong>The object returned by the Date constructor is, by definition, an instance of Date.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> func = () =&gt; { class Animal {}; class Dog extends Animal {}; return checkIfInstanceOf(new Dog(), Animal); }
<strong>Output:</strong> true
<strong>Explanation:</strong>
class Animal {};
class Dog extends Animal {};
checkIfInstanceOf(new Dog(), Animal); // true

Dog is a subclass of Animal. Therefore, a Dog object is an instance of both Dog and Animal.</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> func = () =&gt; checkIfInstanceOf(Date, Date)
<strong>Output:</strong> false
<strong>Explanation: </strong>A date constructor cannot logically be an instance of itself.
</pre>

<p><strong class="example">Example 4:</strong></p>

<pre>
<strong>Input:</strong> func = () =&gt; checkIfInstanceOf(5, Number)
<strong>Output:</strong> true
<strong>Explanation: </strong>5 is a Number. Note that the &quot;instanceof&quot; keyword would return false. However, it is still considered an instance of Number because it accesses the Number methods. For example &quot;toFixed()&quot;.
</pre>

## Solutions

### Solution 1

<!-- tabs:start -->

```ts
function checkIfInstanceOf(obj: any, classFunction: any): boolean {
    if (classFunction === null || classFunction === undefined) {
        return false;
    }
    while (obj !== null && obj !== undefined) {
        const proto = Object.getPrototypeOf(obj);
        if (proto === classFunction.prototype) {
            return true;
        }
        obj = proto;
    }
    return false;
}

/**
 * checkIfInstanceOf(new Date(), Date); // true
 */
```

<!-- tabs:end -->

<!-- end -->
