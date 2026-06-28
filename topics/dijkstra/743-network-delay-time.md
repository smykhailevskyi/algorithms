# [743. Network Delay Time](https://leetcode.com/problems/network-delay-time/description/)  

<code>Medium</code> level  

You are given a network of <code>n</code> nodes, labeled from <code>1</code> to <code>n</code>. You are also given <code>times</code>, a list of travel times as directed edges <code>times[i] = (u<sub>i</sub>, v<sub>i</sub>, w<sub>i</sub>)</code>, where <code>u<sub>i</sub></code> is the source node, <code>v<sub>i</sub></code> is the target node, and <code>w<sub>i</sub></code> is the time it takes for a signal to travel from source to target.  
We will send a signal from a given node <code>k</code>. Return <i>the <strong>minimum</strong> time it takes for all the <code>n</code> nodes to receive the signal</i>. If it is impossible for all the n nodes to receive the signal, return <code>-1</code>.  

<strong>Example 1:</strong>   

<img alt="" src="../../images/dikstra/743-network-delay-time.png" style="height: 220px; width: 200px;" />  

<pre>
<strong>Input:</strong> times = [[2,1,1],[2,3,1],[3,4,1]], n = 4, k = 2
<strong>Output:</strong> 2
</pre>  

<strong>Example 2:</strong>  

<pre>
<strong>Input:</strong> times = [[1,2,1]], n = 2, k = 1
<strong>Output:</strong> 1
</pre>  

<strong>Example 3:</strong> 

<pre>
<strong>Input:</strong> times = [[1,2,1]], n = 2, k = 2
<strong>Output:</strong> -1
</pre>  

<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 <= k <= n <= 100</code></li>
	<li><code>1 <= times.length <= 6000</code></li>
	<li><code>times[i].length == 3</code></li>
	<li><code>1 <= u<sub>i</sub>, v<sub>i</sub> <= n</code></li>
	<li><code>u<sub>i</sub> != v<sub>i</sub></code></li>
	<li><code>0 <= w<sub>i</sub> <= 100</code></li>
	<li>All the pairs <code>(u<sub>i</sub>, v<sub>i</sub>)</code> are <strong>unique</strong>. (i.e., no multiple edges.)</li>
</ul>  
