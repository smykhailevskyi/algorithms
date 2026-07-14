# [3988. Create Grid With Exactly K Paths I](https://leetcode.com/problems/create-grid-with-exactly-k-paths-i/)  

<code>Medium</code> level 

You are given three integers <code>m</code>, <code>n</code>, and <code>k</code>.

Construct **any** <code>m x n</code> grid consisting only of the characters <code>'.'</code> and <code>'#'</code>, where:

* <code>'.'</code> represents a free cell.
* <code>'#'</code> represents an obstacle cell.
A **valid path** is a sequence of free cells that:

* Starts at the top-left cell <code>(0, 0)</code>.
* Ends at the bottom-right cell <code>(m - 1, n - 1)</code>.
* Moves only:
  * Right, from <code>(i, j)</code> to <code>(i, j + 1)</code>, or
  * Down, from <code>(i, j)</code> to <code>(i + 1, j)</code>.  

Return any grid such that there are **exactly** <code>k</code> **valid paths** from the top-left cell to the bottom-right cell. If no such grid exists, return an empty array.


**Example 1:**
<pre>
<strong>Input:</strong> m = 2, n = 3, k = 2
<strong>Output:</strong> ["...","#.."]
</pre>
**Explanation:**

|   .   |  .  |   .   |
| :---: | :-: |  :--: |
|   #   |  . |    .   |


There are exactly <code>k = 2</code> valid paths from <code>(0, 0)</code> to <code>(1, 2)</code>:

* <code>(0, 0) → (0, 1) → (0, 2) → (1, 2)</code>
* <code>(0, 0) → (0, 1) → (1, 1) → (1, 2)</code>  

**Example 2:**
<pre>
<strong>Input:</strong> m = 3, n = 3, k = 4
<strong>Output:</strong> ["..#","...","#.."]
</pre>
**Explanation:**

|   .   |  .  |   #   |
| :---: | :-: |  :--: |
|   .   |  .  |   .   |
|   #   |  .  |   .   |

There are exactly <code>k = 4</code> valid paths from <code>(0, 0)</code> to <code>(2, 2)</code>:

* <code>(0, 0) → (0, 1) → (1, 1) → (1, 2) → (2, 2)</code>
* <code>(0, 0) → (0, 1) → (1, 1) → (2, 1) → (2, 2)</code>
* <code>(0, 0) → (1, 0) → (1, 1) → (1, 2) → (2, 2)</code>
* <code>(0, 0) → (1, 0) → (1, 1) → (2, 1) → (2, 2)</code>

**Example 3:**
<pre>
<strong>Input:</strong> m = 1, n = 4, k = 2
<strong>Output:</strong> []
</pre>
**Explanation:​**

No grid exists with exactly <code>k = 2</code> valid paths for a <code>1 x 4</code> grid, so the answer is an empty array.

<br />

**Constraints:**

* <code>1 <= m, n <= 10</code>
* <code>1 <= k <= 4</code>

