# Binary Search

Given an array of integers nums which is sorted in ascending order, and an integer target, write a function to search target in nums. If target exists, then return its index. Otherwise, return -1.

You must write an algorithm with O(log n) runtime complexity.

```text
Example 1:

Input: nums = [-1,0,3,5,9,12], target = 9
Output: 4
Explanation: 9 exists in nums and its index is 4
Example 2:

Input: nums = [-1,0,3,5,9,12], target = 2
Output: -1
Explanation: 2 does not exist in nums so return -1

Constraints:

1 <= nums.length <= 104
-104 < nums[i], target < 104
All the integers in nums are unique.
nums is sorted in ascending order.
```

## 문제 해결 방법

* 정렬된 배열이 있어야 함

1. 중간값을 찾고 왼쪽과 오른쪽 파티션을 분리한다.
2. 찾을 값이 작을경우 왼쪽, 오른쪽을 좌우로 탐색하면서 결고라를 반환

```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
var search = function(nums, target) {
    let pivot, left = 0, right = nums.length - 1;
    while (left <= right) {
        let mid = left + parseInt((right - left) / 2);
        if (target == nums[mid]) {
            return mid;
        } 
        
        if (target < nums[mid]) {
            right = mid - 1;
        } else {
            left = mid + 1;
        }
    }
    return -1;
};

```
