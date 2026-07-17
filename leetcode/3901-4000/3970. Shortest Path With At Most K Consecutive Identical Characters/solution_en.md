# [3970. Shortest Path With At Most K Consecutive Identical Characters](https://leetcode.com/problems/shortest-path-with-at-most-k-consecutive-identical-characters/)  

<code>Medium</code> level  

You are given an integer <code>n</code> representing the number of nodes in a **directed weighted** graph, numbered from 0 to <code>n - 1</code>. This is represented by a 2D integer array <code>edges</code>, where <code>edges[i] = [u<sub>i</sub>, v<sub>i</sub>, w<sub>i</sub>]</code> represents a directed edge from node <code>u<sub>i</sub></code> to node <code>v<sub>i</sub></code> with weight <code>w<sub>i</sub></code>.

You are also given a string <code>labels</code> of length <code>n</code>, where <code>labels[i]</code> is the character assigned to node <code>i</code>, and an integer <code>k</code>.

Return the **minimum total** edge weight of a path from node 0 to node <code>n - 1</code> such that the concatenation of the labels of the nodes along the path contains **at most** <code>k</code> **consecutive identical** characters. If no valid path exists, return -1.  

**Example 1:**

<pre>
<strong>Input:</strong> n = 3, edges = [[0,1,1],[1,2,1],[0,2,3]], labels = "aab", k = 1
<strong>Output:</strong> 3
</pre>

**Explanation:**

The optimal valid path from node 0 to node 2 is as follows:

<li>Use <code>edges[2] = [0, 2, 3]</code> to reach node 2 with a weight <code>w<sub>i</sub> = 3</code>.</li>  
<br />

The corresponding concatenation of labels is <code>"ab"</code>, which satisfies at most <code>k = 1</code> consecutive identical characters. Thus, the answer is 3.  
<br /> 
<strong>Example 2:</strong>

<pre>
<strong>Input:</strong> n = 3, edges = [[0,1,1],[1,2,1],[0,2,3]], labels = "aab", k = 2
<strong>Output:</strong> 2
</pre>  

<strong>Explanation:</strong>

The optimal valid path from node 0 to node 2 is as follows:

<li>Use <code>edges[0] = [0, 1, 1]</code> to reach node 1 with weight <code>w<sub>i</sub> = 1</code>.</li>
<li>Use <code>edges[1] = [1, 2, 1]</code> to reach node 2 with weight <code>w<sub>i</sub> = 1</code>.</li>  
<br />

The corresponding concatenation of labels is <code>"aab"</code>, which satisfies at most <code>k = 2</code> consecutive identical characters. Thus, the answer is 2.

**Example 3:**

<pre>
<strong>Input:</strong> n = 3, edges = [[0,1,1],[1,2,1]], labels = "aaa", k = 2
<strong>Output:</strong> -1
</pre>

<strong>Explanation:</strong>

There is no valid path from node 0 to node 2 that satisfies at most <code>k = 2</code> consecutive identical characters. Thus, the answer is -1.  

**Constraints:**

<li><code>1 <= n == labels.length <= 5 * 10<sup>4</sup></code></li>
<li><code>0 <= edges.length <= 5 * 10<sup>4</sup></code></li>
<li><code>edges[i] == [u<sub>i</sub>, v<sub>i</sub>, w<sub>i</sub>]</code></li>
<li><code>0 <= u<sub>i</sub>, v<sub>i</sub> <= n - 1</code></li>
<li><code>u<sub>i</sub> != v<sub>i</sub></code></li>
<li><code>1 <= w<sub>i</sub> <= 10<sup>4</sup></code></li>
<li><code>labels</code> consists of lowercase English letters</li>
<li><code>1 <= k <= 50</code></li>  
<br/>

***

### Solution  

<strong>Time complexity</strong>:  <code> O(E × K × log(V × K))</code>  
<strong>Space complexity</strong>: <code> O(V × K + E)</code>  
**where**:  
<code>E</code> - кількість ребер графа  
<code>V</code> - кількість вершин графа  
<code>K</code> - максимальна дозволена кількість однакових символів поспіль  


```C++
class Solution {
public:
    int shortestPath(int n, vector<vector<int>>& edges, string labels, int k) {
      vector<vector<pair<int, int>>> graph(n);

      for (const auto& edge : edges) {
        int u = edge[0];
        int v = edge[1];
        int weight = edge[2];

        graph[u].push_back({v, weight});
      }

      const long long INF = LLONG_MAX / 4;

      vector<vector<long long>> dist(n, vector<long long>(k + 1, INF));

      using State = tuple<long long, int, int>;

      priority_queue<State, vector<State>, greater<State>> pq;

      dist[0][1] = 0;
      pq.push({0, 0, 1});

      while (!pq.empty()) {
        auto [currentDist, u, count] = pq.top();
        pq.pop();

        if (currentDist != dist[u][count]) {
          continue;
        }

        if (u == n - 1) {
          return static_cast<int>(currentDist);
        }

        for (auto [v, weight] : graph[u]) {
          int newCount;

          if (labels[u] == labels[v]) {
            newCount = count + 1;
          } else {
            newCount = 1;
          }

          if (newCount > k) {
            continue;
          }

          long long newDist = currentDist + weight;

          if (newDist < dist[v][newCount]) {
            dist[v][newCount] = newDist;
            pq.push({newDist, v, newCount});
          }
        }
      }

      return -1;
    }
};
```