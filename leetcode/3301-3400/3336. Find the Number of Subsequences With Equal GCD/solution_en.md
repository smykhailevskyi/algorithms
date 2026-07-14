# [3336. Find the Number of Subsequences With Equal GCD](https://leetcode.com/problems/find-the-number-of-subsequences-with-equal-gcd/description/)  

<code>Hard</code> level 

You are given an integer array <code>nums</code>.

Your task is to find the number of pairs of **non-empty** **subsequences** <code>(seq1, seq2)</code> of <code>nums</code> that satisfy the following conditions:

<li>The subsequences <code>seq1</code> and <code>seq2</code> are <strong>disjoint</strong>, meaning <strong>no index of</strong> <code>nums</code> is common between them.</li>
<li>The <strong>GCD</strong> of the elements of <code>seq1</code> is equal to the GCD of the elements of <code>seq2</code>.</li>
Return the total number of such pairs.

<br />
Since the answer may be very large, return it <strong>modulo</strong> <code>10<sup>9</sup> + 7</code>.

<br />

**Example 1:**
<pre>
<strong>Input:</strong> nums = [1,2,3,4]

<strong>Output:</strong> 10
</pre>

<strong>Explanation:</strong>

The subsequence pairs which have the GCD of their elements equal to 1 are:

<li><code>([<ins>1</ins>, 2, 3, 4], [1, <ins>2</ins>, <ins>3</ins>, 4])</li></code>
<li><code>([<ins>1</ins>, 2, 3, 4], [1, <ins>2</ins>, <ins>3</ins>, <ins>4</ins>])</li></code>
<li><code>([<ins>1</ins>, 2, 3, 4], [1, 2, <ins>3</ins>, <ins>4</ins>])</li></code>
<li><code>([<ins>1</ins>, <ins>2</ins>, 3, 4], [1, 2, <ins>3</ins>, <ins>4</ins>])</li></code>
<li><code>([<ins>1</ins>, 2, 3, <ins>4</ins>], [1, <ins>2</ins>, <ins>3</ins>, 4])</li></code>
<li><code>([1, <ins>2</ins>, <ins>3</ins>, 4], [<ins>1</ins>, 2, 3, 4])</li></code>
<li><code>([1, <ins>2</ins>, <ins>3</ins>, 4], [<ins>1</ins>, 2, 3, <ins>4</ins>])</li></code>
<li><code>([1, <ins>2</ins>, <ins>3</ins>, <ins>4</ins>], [<ins>1</ins>, 2, 3, 4])</li></code>
<li><code>([1, 2, <ins>3</ins>, <ins>4</ins>], [<ins>1</ins>, 2, 3, 4])</li></code>
<li><code>([1, 2, <ins>3</ins>, <ins>4</ins>], [<ins>1</ins>, <ins>2</ins>, 3, 4])</li></code>  
<br />
<strong>Example 2:</strong>  

<br />
<pre>
<strong>Input:</strong> nums = [10,20,30]

<strong>Output:</strong> 2
</pre>

<strong>Explanation:</strong>

The subsequence pairs which have the GCD of their elements equal to 10 are:

<li><code>([<ins>10</ins>, 20, 30], [10, <ins>20</ins>, <ins>30</ins>])</li></code>
<li><code>([10, <ins>20</ins>, <ins>30</ins>], [<ins>10</ins>, 20, 30])</li></code>  
<br />
<strong>Example 3:</strong>

<br />
<pre>
<strong>Input:</strong> nums = [1,1,1,1]

<strong>Output:</strong> 50
</pre>

<strong>Constraints:</strong>

<li><code>1 <= nums.length <= 200</li></code>
<li><code>1 <= nums[i] <= 200</li></code>
<br />

***

<h3>Solution</h3>  
<strong>if:</strong>

```C++
n = nums.size();
M = max(nums);
``` 

<strong>Time complexity</strong>:  <code> O(n * M<sup>2</sup> * logM)</code>  
<strong>Space complexity</strong>: <code> O(M<sup>2</sup>)</code>

**C++**
```C++
class Solution {
public:
  int subsequencePairCount(vector<int>& nums) {
    static constexpr int MOD = 1000000007;
    int maxValue = *max_element(nums.begin(), nums.end());

    vector<vector<int>> dp(maxValue + 1, vector<int>(maxValue + 1, 0));
    dp[0][0] = 1;

    for (int x : nums) {
        vector<vector<int>> next(maxValue + 1, vector<int>(maxValue + 1, 0));

        for (int g1 = 0; g1 <= maxValue; g1++) {
          for (int g2 = 0; g2 <= maxValue; g2++) {
            int ways = dp[g1][g2];

            if (ways == 0) {
                continue;
            }

            next[g1][g2] = (next[g1][g2] + ways) % MOD;
            int newG1 = std::gcd(g1, x);

            next[newG1][g2] = (next[newG1][g2] + ways) % MOD;
            int newG2 = std::gcd(g2, x);

            next[g1][newG2] = (next[g1][newG2] + ways) % MOD;
          }
        }

        dp = move(next);
    }

    long long answer = 0;

    for (int g = 1; g <= maxValue; g++) {
        answer += dp[g][g];
        answer %= MOD;
    }

    return static_cast<int>(answer);
  }
};
```