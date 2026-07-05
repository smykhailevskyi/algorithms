# [3978. Unique Middle Element](https://leetcode.com/problems/unique-middle-element/)  

<code>Easy</code> level  

You are given an integer array <code>nums</code> of odd length <code>n</code>.

Return <code>true</code> if the middle element of <code>nums</code> appears **exactly** once in the array. Otherwise return <code>false</code>.  

**Example 1:**
<pre>
<strong>Input</strong>: nums = [1,2,3]
<strong>Output</strong>: true
</pre>
**Explanation:**

The middle element of <code>nums</code> is 2, which appears exactly once.

Thus, the answer is <code>true</code>.  

**Example 2:**
<pre>
<strong>Input</strong>: nums = [1,2,2]
<strong>Output</strong>: false
</pre>
**Explanation:**

The middle element of <code>nums</code> is 2, which appears twice.

Thus, the answer is <code>false</code>.  

**Constraints:**

<li><code>1 <= n == nums.length <= 100</code></li>
<li><code>n</code> is odd.</li>
<li><code>1 <= nums[i] <= 100</code></li>  
<br />

***

<h3>Solution</h3>  

<strong>Time complexity</strong>:  <code> O(n)</code>  
<strong>Space complexity</strong>: <code> O(1)</code>

**C++**
```C++
class Solution {
public:
    bool uniqueMiddleElement(vector<int>& nums) {
        int middle = nums[nums.size() / 2];

        int count = 0;

        for (int num : nums) {
            if (num == middle)
                count++;
        }

        return count == 1;
    }
};
```

A shorter but maybe less readable solution by using <code>std::count()</code> STL algorithm
```C++
class Solution {
public:
    bool uniqueMiddleElement(vector<int>& nums) {
        return count(nums.begin(), nums.end(), nums[nums.size() / 2]) == 1;
    }
};
```
