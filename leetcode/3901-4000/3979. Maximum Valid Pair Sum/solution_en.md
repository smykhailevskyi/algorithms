# [3979. Maximum Valid Pair Sum](https://leetcode.com/problems/maximum-valid-pair-sum/description/)  

<code>Medium</code> level 

You are given an integer array <code>nums</code> of length <code>n</code> and an integer <code>k</code>.

A pair of indices <code>(i, j)</code> is called <strong>valid</strong> if:

<li><code>0 <= i < j < n</li></code>
<li><code>j - i >= k</li></code>  
<br />
Return the <strong>maximum</strong> value of <code>nums[i] + nums[j]</code> among all valid pairs.  

<br />  

**Example 1:**
<pre>
<strong>Input</strong>: nums = [1,3,5,2,8], k = 2
<strong>Output</strong>: 13
</pre>
**Explanation:**

The valid pairs are:

<li><code>(0, 2): nums[0] + nums[2] = 6</code></li>
<li><code>(0, 3): nums[0] + nums[3] = 3</code></li>
<li><code>(0, 4): nums[0] + nums[4] = 9</code></li>
<li><code>(1, 3): nums[1] + nums[3] = 5</code></li>
<li><code>(1, 4): nums[1] + nums[4] = 11</code></li>
<li><code>(2, 4): nums[2] + nums[4] = 13</code></li>  
<br />
Thus, the answer is 13.​​​​​​​

<br />

**Example 2:**
<pre>
<strong>Input</strong>: nums = [5,1,9], k = 1
<strong>Output</strong>: 14
</pre>
**Explanation:**

<li>Since <code>k = 1</code>, every pair is valid.</li>
<li>The maximum value is obtained from a pair <code>(0, 2)</code>​​​​​​​, which is <code>nums[0] + nums[2] = 5 + 9 = 14</code>.</li>
<li>Thus, the answer is 14.</li>  
<br />

**Constraints:**

<li><code>2 <= n == nums.length <= 10<sup>5</sup></code></li>
<li><code>1 <= nums[i] <= 10<sup>9</sup></code></li>
<li><code>1 <= k <= n - 1</code></li> 
<br />

***

<h3>Solution</h3>  

<strong>Time complexity</strong>:  <code> O(n)</code>  
<strong>Space complexity</strong>: <code> O(1)</code>

**C++**
```C++
class Solution {
public:
  int maximumValidPairSum(vector<int>& nums, int k) {
    int n = nums.size();

    int maxLeft = INT_MIN;
    int answer = INT_MIN;

    for (int j = k; j < n; j++) {
        maxLeft = max(maxLeft, nums[j - k]);
        answer = max(answer, maxLeft + nums[j]);
    }

    return answer;
  }
};
```