# [3987. Minimum Total Cost to Process All Elements](https://leetcode.com/problems/minimum-total-cost-to-process-all-elements/)  

<code>Medium</code> level 

You are given an integer array <code>nums</code> and an integer <code>k</code>.

Initially, you have <code>k</code> units of resources.

You must process the elements of <code>nums</code> from left to right. To process the <code>i<sup>th</sup></code> element, you need <code>nums[i]</code> resources.

If your available resources are less than <code>nums[i]</code>, you may perform an operation that increases your available resources by <code>k</code>. The value of <code>k</code> is fixed and does not change throughout the process. The first such operation incurs a cost of 1, the second incurs a cost of 2, and so on.

After processing the <code>i<sup>th</sup></code> element, your available resources decrease by <code>nums[i]</code>.

Return an integer denoting the **minimum total cost** required to process all elements. Since the answer may be very large, return it **modulo** <code>10<sup>9</sup> + 7</code>.  

<br />

**Example 1:**
<pre>
<strong>Input:</strong> nums = [1,2,3,4], k = 4
<strong>Output:</strong> 3
</pre>
**Explanation:**

* After processing <code>nums[0]</code>, we have <code>4 - 1 = 3</code> units of resources left.
* After processing <code>nums[1]</code>, we have <code>3 - 2 = 1</code> unit of resources left.
* Since <code>nums[2] = 3</code> and only 1 unit of resources is available, we perform the first operation costing 1. After processing <code>nums[2]</code>, we have <code>1 + 4 - 3 = 2</code> units of resources left.
* Since <code>nums[3] = 4</code> and only 2 units of resources are available, we perform the second operation costing 2, to have <code>2 + 4 = 6</code> units of resources, which is enough to process <code>nums[3]</code>.
* Thus, the total cost is <code>1 + 2 = 3</code>.  

**Example 2:**
<pre>
<strong>Input:</strong> nums = [1,1,7,14], k = 4
<strong>Output:</strong> 15
</pre>
**Explanation:**

* After processing <code>nums[0]</code>, we have <code>4 - 1 = 3</code> units of resources left.
* After processing <code>nums[1]</code>, we have <code>3 - 1 = 2</code> units of resources left.
* Since <code>nums[2] = 7</code> and only 2 units of resources are available, we perform two operations costing <code>1 + 2 = 3</code>. After processing <code>nums[2]</code>, we have <code>2 + 4 + 4 - 7 = 3</code> units of resources left.
* Since <code>nums[3] = 14</code> and only 3 units of resources are available, we perform three operations costing <code>3 + 4 + 5 = 12</code>, to have <code>3 + 4 + 4 + 4 = 15</code> units of resources, which is enough to process <code>nums[3]</code>.
* Thus, the total cost is <code>3 + 12 = 15</code>.  

**Example 3:**
<pre>
<strong>Input:</strong> nums = [1,2,3,4], k = 10
<strong>Output:</strong> 0
</pre>
**Explanation:**

To process all elements, we can use the initial 10 units of resources without performing any operations. Thus, the total cost required is 0.  

<br />

**Constraints:**

* <code>1 <= nums.length <= 10<sup>5</sup></code>
* <code>1 <= nums[i] <= 10<sup>9</sup></code>
* <code>1 <= k <= 10<sup>9</sup></code>