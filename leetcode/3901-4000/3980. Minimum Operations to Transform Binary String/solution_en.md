# [3980. Minimum Operations to Transform Binary String](https://leetcode.com/problems/minimum-operations-to-transform-binary-string/description/)  

<code>Medium</code> level 

You are given two **binary strings** <code>s1</code> and <code>s2</code> of the same length <code>n</code>.

You can perform the following operations on <code>s1</code> any number of times, in any order:

<li>Choose an index <code>i</code> such that <code>s1[i] == '0'</code>, and change it to <code>'1'</code>.</li>
<li>Choose an index <code>i</code> such that <code>0 <= i < n - 1</code>, and both <code>s1[i]</code> and <code>s1[i + 1]</code> are <code>'1'</code>. Change both characters to <code>'0'</code>.</li>  
<br />
  
Return the <strong>minimum</strong> number of operations required to make <code>s1</code> equal to <code>s2</code>. If it is impossible, return -1.      

<strong>Example 1:</strong>

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
<br />

***

### Solution

**Time complexity:** <code>O(n)</code>  
**Space complexity:** <code>O(1)</code>


**C++**
```C++
class Solution {
public:
    int minOperations(string s1, string s2) {
      const int INF = 1e9;
      int n = s1.size();
      int dp[2] = { INF, INF };
      dp[s1[0] - '0'] = 0;

      for (int i = 0; i < n - 1; i++) {
          int nextDp[2] = {INF, INF};

          int nextBit = s1[i + 1] - '0';
          int target = s2[i] - '0';

        for (int current = 0; current <= 1; current++) {
          if (dp[current] == INF) continue;

          if (current <= target) {
              int cost = target - current;

              nextDp[nextBit] = min(nextDp[nextBit], dp[current] + cost);
          }

          int cost = 1;

          if (current == 0) {
              cost++;
          }

          if (nextBit == 0) {
              cost++;
          }

          if (target == 1) {
              cost++;
          }

          nextDp[0] = min(nextDp[0], dp[current] + cost);
        }

        dp[0] = nextDp[0];
        dp[1] = nextDp[1];
      }

      int target = s2[n - 1] - '0';
      int answer = INF;

      for (int current = 0; current <= 1; current++) {
        if (current <= target) {
          answer = min(answer, dp[current] + target - current);
        }
      }

      return answer == INF ? -1 : answer;
    }
};
```
