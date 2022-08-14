# Given the root of a binary tree, collect a tree's nodes as if you were doing 

``` text
this:

Collect all the leaf nodes.
Remove all the leaf nodes.
Repeat until the tree is empty.

Example 1:



Input: root = [1,2,3,4,5]
Output: [[4,5,3],[2],[1]]
Explanation:
[[3,5,4],[2],[1]] and [[3,4,5],[2],[1]] are also considered correct answers since per each level it does not matter the order on which elements are returned.
```

![](https://assets.leetcode.com/uploads/2021/03/16/remleaves-tree.jpg)

## 아이디어

  1. 깊이 우선 탐색을 고려하고
  2. 각 노드의 높이를 구하여 높이를 키를 가진 배열 값을 반환 해준다.
  3. 높이는 왼쪽,오른쪽 노드의 합계가 된다.

## 코드

  ```javascript
/**
 * Definition for a binary tree node.
 * function TreeNode(val, left, right) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.left = (left===undefined ? null : left)
 *     this.right = (right===undefined ? null : right)
 * }
 */
/**
 * @param {TreeNode} root
 * @return {number[][]}
 */



var findLeaves = function(root) {
    const result = [];
    
    searchHeight(root, result);
    
    return result;
};

function searchHeight(node, result) {
    //루트 노드는 0부터 시작 한다.
    if (node == null) {
        return -1;    
    }
    
    
//     2
//    1 0
//   0 0 0
    
    const leftHeight = searchHeight(node.left, result);
    const rightHeight = searchHeight(node.right, result);
    
    // 현재의 높이는 리프노드의 최대 값 보다 1 크다
    const height = Math.max(leftHeight, rightHeight) + 1;
    
    if (height == result.length) {
        result.push([]);
    }
    
    
    let arr = result[height];
    arr.push(node.val);
    result[height] = arr;
    
    
    return height;

}

  ```
