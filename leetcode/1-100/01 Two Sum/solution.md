# [1. Two Sum](https://leetcode.com/problems/two-sum/description/)  

Рішення, гарне по Space complexity, але погане по Time complexety.  
Space complexity: O(1)  
Time complexity: O(n<sup>2</sup>)  

#### JavaScript
```js
const twoSum = (nums, target) => {
  for (let i = 0; i < nums.length; i++) {
    for (let j = i + 1; j < nums.length; j++) {
      if (nums[i] + nums[j] === target) {
        return [i, j];
      }
    }
  }
}
```  

Рішення з введенням Hash Map. Покращує Time complexity, але погіршує Space complexity.   
Space complexity: O(n)  
Time complexity: O(n)
#### JavaScript

```js
const twoSum = (nums, target) => {
  const obj = {};

  for(let i = 0; i < nums.length; i++) {
      let val = target - nums[i];

      if(val in obj) {
          return [obj[val], i];
      } else {
          obj[nums[i]] = i;
      }
  }
}
```  
#### C++
```C++
class Solution {
public:
  vector<int> twoSum(vector<int>& nums, int target) {
    std::unordered_map<int, int> map;
  
    for (int i = 0; i < nums.size(); i++) {
      int val = target - nums.at(i);
          
      auto it = map.find(val);
          
      if (it != map.end()) {
          return {it->second, i};
      } else {
          map[nums[i]] = i;
      }
    }
    
    return {};
  }
};
```

