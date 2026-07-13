# [3889. Mirror Frequency Distance](https://leetcode.com/problems/mirror-frequency-distance/description/)  

<code>Medium</code> level 

***

<h3>Solution</h3>  

<strong>Time complexity</strong>:  <code> O(n)</code>  
<strong>Space complexity</strong>: <code> O(1)</code>

**C++**
```C++
class Solution {
public:
  int mirrorFrequency(string s) {
    int answer = 0;
    vector<int> freq(128, 0);

    for (char c : s) {
        freq[c]++;
    }

    for (char c='a'; c<='m'; c++) {
        char mirror = 'z' - (c - 'a');

        answer += abs(freq[c] - freq[mirror]);
    }

    for (char c='0'; c<='4'; c++) {
        char mirror = '9' - (c - '0');

        answer += abs(freq[c] - freq[mirror]);
    }

    return answer;
  }
};
```