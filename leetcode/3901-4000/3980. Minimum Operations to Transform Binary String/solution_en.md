# [3980. Minimum Operations to Transform Binary String](https://leetcode.com/problems/minimum-operations-to-transform-binary-string/description/)  

<code>Medium</code> level 

You are given two **binary strings** <code>s1</code> and <code>s2</code> of the same length <code>n</code>.

You can perform the following operations on <code>s1</code> any number of times, in any order:

<li>Choose an index <code>i</code> such that <code>s1[i] == '0'</code>, and change it to <code>'1'</code>.</li>
<li>Choose an index <code>i</code> such that <code>0 <= i < n - 1</code>, and both <code>s1[i]</code> and <code>s1[i + 1]</code> are <code>'1'</code>. Change both characters to <code>'0'</code>.</li>  
<br />
Return the <strong>minimum</strong> number of operations required to make <code>s1</code> equal to <code>s2</code>. If it is impossible, return -1.  

<br/>

**Example 1:**

<pre>
<strong>Input:</strong> s1 = "11", s2 = "00"
<strong>Output:</strong> 1
</pre>

**Explanation:**

Change indices 0 and 1 from <code>'1'</code> to <code>'0'</code> in one operation, so <code>"11"</code> becomes <code>"00"</code>. Thus, the answer is 1.  

**Example 2:**

<pre>
<strong>Input:</strong> s1 = "01", s2 = "10"
<strong>Output:</strong> 3
</pre>

**Explanation:**

<li>Change index 0 from <code>'0'</code> to <code>'1'</code>, so <code>"01"</code> becomes <code>"11"</code>.</li>
<li>Change indices 0 and 1 from <code>'1'</code> to <code>'0'</code>, so <code>11"</code> becomes <code>"00"</code>.</li>
<li>Change index 0 from <code>'0'</code> to <code>'1'</code>, so <code>"00"</code> becomes <code>"10"</code>.</li>
<li>Thus, the answer is 3.</li>  

<br />

**Example 3:**

<pre>
<strong>Input:</strong> s1 = "1", s2 = "0"
<strong>Output:</strong> -1
</pre>
**Explanation:**

The first operation cannot change <code>'1'</code> to <code>'0'</code>, and the second operation requires two adjacent characters. Therefore, it is impossible.

**Constraints:**

<li><code>1 <= n == s1.length == s2.length <= 10<sup>5</sup></code></li>
<li><code>s1</code> and <code>s2</code> consist only of <code>'0'</code> and <code>'1'</code>.</li>