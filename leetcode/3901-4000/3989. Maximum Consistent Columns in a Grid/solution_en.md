# [3989. Maximum Consistent Columns in a Grid](https://leetcode.com/problems/maximum-consistent-columns-in-a-grid/)  

<code>Hard</code> level 

You are given a 2D integer array <code>grid</code> of size <code>m x n</code>, and an integer <code>limit</code>.

You may remove zero or more columns from the grid, but at least one column must remain. The **relative** order of the remaining columns must be preserved.

A grid is called **consistent** if for every row <code>i</code>, and for every pair of adjacent remaining columns <code>a</code> and <code>b</code> with <code>a < b</code>, the following holds: <code>|grid[i][b] - grid[i][a]| <= limit</code>.

Return the **maximum** number of columns that can remain such that the resulting grid is **consistent**.  

<br />

**Example 1:**
<pre>
<strong>Input:</strong> grid = [[-2,0,3]], limit = 2
<strong>Output:</strong> 2
</pre>
**Explanation:**

Remove column 2 and keep columns 0 and 1, which gives <code>|grid[0][1] − grid[0][0]| = |0 − (−2)| = 2 <= limit</code>.
Thus, the maximum number of columns that can remain is 2.  

**Example 2:**
<pre>
<strong>Input:</strong> grid = [[1,-1,1],[2,2,2]], limit = 1
<strong>Output:</strong> 2
</pre>
**Explanation:**

* Remove column 1 and keep columns 0 and 2, which gives
  * <code>|grid[0][2] − grid[0][0]| = |1 − 1| = 0 <= limit</code> and
  * <code>|grid[1][2] − grid[1][0]| = |2 − 2| = 0 <= limit</code>.
* Thus, the maximum number of columns that can remain is 2.  

**Example 3:**
<pre>
<strong>Input:</strong> grid = [[-5,5]], limit = 9
<strong>Output:</strong> 1
</pre>
**Explanation:**

* Remove either column 0 or column 1, since <code>|grid[0][1] − grid[0][0]| = |5 − (−5)| = 10 > limit</code>.
* Thus, the maximum number of columns that can remain is 1.  

<br />

**Constraints:**

* <code>1 <= m == grid.length <= 250</code>
* <code>1 <= n == grid[i].length <= 250</code>
* <code>-10<sup>5</sup> <= grid[i][j] <= 10<sup>5</sup></code>
* <code>0 <= limit <= 10<sup>5</sup></code>

