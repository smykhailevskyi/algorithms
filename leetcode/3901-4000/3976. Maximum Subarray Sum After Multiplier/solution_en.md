# [3976. Maximum Subarray Sum After Multiplier](https://leetcode.com/problems/maximum-subarray-sum-after-multiplier/)  

<code>Medium</code> level  

You are given an integer array <code>nums</code> and a positive integer <code>k</code>.  
You must choose <strong>exactly</strong> one <strong>subarray</strong> of <code>nums</code> and perform <strong>exactly</strong> one of the following operations:  
1. Multiply each number in the chosen subarray by <code>k</code>.
2. Divide each number in the chosen subarray by <code>k</code>.
<li>When dividing a positive number by <code>k</code>, use the <strong>floor</strong> value of the division result.</li>
<li>When dividing a negative number by <code>k</code>, use the <strong>ceiling</strong> value of the division result.</li>  
Return the <strong>maximum</strong> possible sum of a <strong>non-empty</strong> subarray in the resulting array.  
Note that the subarray chosen for the operation and the subarray chosen for the sum may be <strong>different</strong>.  
 
<br />
<strong>Example 1:</strong>  
<pre>
<strong>Input:</strong> nums = [1,-2,3,4,-5], k = 2  
<strong>Output:</strong> 14  
</pre>
<strong>Explanation:</strong>  

<li>Multiply each number in the subarray <code>[3, 4]</code> by 2.</li>
<li>This results in <code>nums = [1, -2, 6, 8, -5]</code>.</li>
<li>The subarray with the largest sum is <code>[6, 8]</code>, so the output is <code>6 + 8 = 14</code>.</li>  
<br/>
<strong>Example 2:</strong>  
<pre>
<strong>Input</strong>: nums = [-5,-4,-3], k = 2  
<strong>Output</strong>: -1
</pre>  

<strong>Explanation:</strong>  
<li>Divide each number in the subarray <code>[-3]</code> by 2.</li>
<li>This results in <code>nums = [-5, -4, -1]</code>.</li>
<li>he subarray with the largest sum is <code>[-1]</code>, so the output is -1.</li>  
<br />
<strong>Constraints:</strong>

<li><code>1 <= nums.length <= 105</code></li>
<li><code>-105 <= nums[i] <= 105</code></li>
<li><code>1 <= k <= 105</code></li>   

***


<h3>Solution</h3>  

<strong>C++</strong>  
```C++

```
