# [3981. Count Distinct Ways to Form Target from Two Strings](https://leetcode.com/problems/count-distinct-ways-to-form-target-from-two-strings/)  

<code>Hard</code> level 

You are given three strings <code>word1</code>, <code>word2</code>, and <code>target</code>.

Your task is to count the number of ways to form <code>target</code> by choosing characters from <code>word1</code> and <code>word2</code> under the following conditions:

<li>For each character of <code>target</code>, choose one matching character from either <code>word1</code> or <code>word2</code>.</li> 
<li>The chosen indices from <code>word1</code> must be <strong>strictly</strong> increasing.</li>
<li>The chosen indices from <code>word2</code> must be <strong>strictly</strong> increasing.</li>
<li><strong>At least</strong> one character must be chosen from <strong>both</strong> <code>word1</code> and <code>word2</code>.</li>
<br />

Two ways are considered different if, for <strong>at least</strong> one position in <code>target</code>, the chosen character comes from a different string or a different index.
<br />

Return the number of ways. Since the answer may be very large, return it <strong>modulo</strong> <code>10<sup>9</sup> + 7</code>.  
<br />
**Example 1:**

<pre>
<strong>Input:</strong> word1 = "abc", word2 = "bac", target = "abc"
<strong>Output:</strong> 5
</pre>
**Explanation:**

There are 5 ways to form <code>target</code>:

<li><code>word1[0] = 'a'</code>, <code>word1[1] = 'b'</code>, <code>word2[2] = 'c'</code></li>
<li><code>word1[0] = 'a'</code>, <code>word2[0] = 'b'</code>, <code>word1[2] = 'c'</code></li>
<li><code>word1[0] = 'a'</code>, <code>word2[0] = 'b'</code>, <code>word2[2] = 'c'</code></li>
<li><code>word2[1] = 'a'</code>, <code>word1[1] = 'b'</code>, <code>word1[2] = 'c'</code></li>
<li><code>word2[1] = 'a'</code>, <code>word1[1] = 'b'</code>, <code>word2[2] = 'c'</code></li>
<br />

All ways preserve the increasing index order inside each string and choose at least one character from each string.  
<br />
**Example 2:**

<pre>
<strong>Input:</strong> word1 = "cd", word2 = "cd", target = "ccd"
<strong>Output:</strong> 4
</pre>
**Explanation:**

There are 4 ways to form <code>target</code>:

<li><code>word1[0] = 'c'</code>, <code>word2[0] = 'c'</code>, <code>word1[1] = 'd'</code></li>
<li><code>word1[0] = 'c'</code>, <code>word2[0] = 'c'</code>, <code>word2[1] = 'd'</code></li>
<li><code>word2[0] = 'c'</code>, <code>word1[0] = 'c'</code>, <code>word1[1] = 'd'</code></li>
<li><code>word2[0] = 'c'</code>, <code>word1[0] = 'c'</code>, <code>word2[1] = 'd'</code></li>
<br />

The first two <code>'c'</code> characters in <code>target</code> must come one from each string. The final <code>'d'</code> can be chosen from either string.

**Example 3:**
<pre>
<strong>Input:</strong> word1 = "xy", word2 = "xy", target = "xyxy"
<strong>Output:</strong> 2
</pre>
**Explanation:**

There are 2 ways to form <code>target</code>:

<li><code>word1[0] = 'x'</code>, <code>word1[1] = 'y'</code>, <code>word2[0] = 'x'</code>, <code>word2[1] = 'y'</code></li>
<li><code>word2[0] = 'x'</code>, <code>word2[1] = 'y'</code>, <code>word1[0] = 'x'</code>, <code>word1[1] = 'y'</code></li>
<br/>

Each <code>"xy"</code> part in <code>target</code> comes entirely from one string. 
<br />

**Example 4:**
<pre>
<strong>Input:</strong> word1 = "ab", word2 = "cde", target = "ace"
<strong>Output:</strong> 1
</pre>
**Explanation:**

The only way is to choose <code>word1[0] = 'a'</code>, <code>word2[0] = 'c'</code>, and <code>word2[2] = 'e'</code>. Thus, the answer is 1.  

**Constraints:**

<li><code>1 <= word1.length, word2.length, target.length <= 100</code></li>
<li><code>word1</code>, <code>word2</code>, and target consist of lowercase English letters only.</li>
<br />

***

### Solution

**Time complexity:**  <code>O(n<sup>3</sup>)</code>  
**Space complexity:**  <code>O(n<sup>2</sup>)</code>  

**C++**

```C++
class Solution {
public:
    static constexpr int MOD = 1000000007;

    int interleaveCharacters(string word1, string word2, string target) {
      int n = word1.size();
      int m = word2.size();

      vector<vector<array<long long, 4>>> dp(n + 1, vector<array<long long, 4>>(m + 1));
      dp[0][0][0] = 1;

      for (char targetChar : target) {
        vector<vector<array<long long, 4>>> next(n + 1, vector<array<long long, 4>>(m + 1));

        for (int j = 0; j <= m; ++j) {
          array<long long, 4> prefix = {};

          for (int p = 0; p < n; ++p) {
            for (int mask = 0; mask < 4; ++mask) {
              prefix[mask] += dp[p][j][mask];
              prefix[mask] %= MOD;
            }

            if (word1[p] != targetChar) {
              continue;
            }

            for (int mask = 0; mask < 4; ++mask) {
              int newMask = mask | 1;

              next[p + 1][j][newMask] += prefix[mask];
              next[p + 1][j][newMask] %= MOD;
            }
          }
        }

        for (int i = 0; i <= n; ++i) {
          array<long long, 4> prefix = {};

          for (int q = 0; q < m; ++q) {
            for (int mask = 0; mask < 4; ++mask) {
              prefix[mask] += dp[i][q][mask];
              prefix[mask] %= MOD;
            }

            if (word2[q] != targetChar) {
              continue;
            }

            for (int mask = 0; mask < 4; ++mask) {
              int newMask = mask | 2;

              next[i][q + 1][newMask] += prefix[mask];
              next[i][q + 1][newMask] %= MOD;
            }
          }
        }

        dp = move(next);
      }

      long long answer = 0;

      for (int i = 0; i <= n; ++i) {
        for (int j = 0; j <= m; ++j) {
          answer += dp[i][j][3];
          answer %= MOD;
        }
      }

      return static_cast<int>(answer);
    }
};
```
