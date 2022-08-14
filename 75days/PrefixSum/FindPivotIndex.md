# Find Pivot Index

Given an array of integers nums, calculate the pivot index of this array.

The pivot index is the index where the sum of all the numbers strictly to the left of the index is equal to the sum of all the numbers strictly to the index's right.

If the index is on the left edge of the array, then the left sum is 0 because there are no elements to the left. This also applies to the right edge of the array.

Return the leftmost pivot index. If no such index exists, return -1.

> 요약  
> 배열이 주어지고 해당 축값을 기준으로 축을 제외한 왼쪽, 오른쪽 배열들의 값이 같은 인덱스를 구해라

``` text
Example 1:

Input: nums = [1,7,3,6,5,6]
Output: 3
Explanation:
The pivot index is 3.
Left sum = nums[0] + nums[1] + nums[2] = 1 + 7 + 3 = 11
Right sum = nums[4] + nums[5] = 5 + 6 = 11
Example 2:

Input: nums = [1,2,3]
Output: -1
Explanation:
There is no index that satisfies the conditions in the problem statement.
Example 3:

Input: nums = [2,1,-1]
Output: 0
Explanation:
The pivot index is 0.
Left sum = 0 (no elements to the left of index 0)
Right sum = nums[1] + nums[2] = 1 + -1 = 0
 

Constraints:

1 <= nums.length <= 104
-1000 <= nums[i] <= 1000

```

## 아이디어

1. 합계를 구하여 왼쪽 배열의 값은 순차적으로 순회한 배열의 합
2. 해당 합계, 축의 값을빼면 오른쪽 배열의 합이 구해진다.
3. 같을 때 인덱스를 리턴!

### 풀이

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var pivotIndex = function(nums) {
    let leftSum = 0;
    const sum = nums.reduce((init = 0,curr) => init + curr);
    
    for (let i = 0; i < nums.length; i++) {
        let left = leftSum;
        let right = sum - nums[i] - leftSum;
        leftSum += nums[i];
        if (left === right) {
            return i;
        }
    }
    return -1;
    
};

```
