# Merge Two Sorted Lists

You are given the heads of two sorted linked lists list1 and list2.

Merge the two lists in a one sorted list. The list should be made by splicing together the nodes of the first two lists.

Return the head of the merged linked list.

```text
Example 1:

Input: list1 = [1,2,4], list2 = [1,3,4]
Output: [1,1,2,3,4,4]
Example 2:

Input: list1 = [], list2 = []
Output: []
Example 3:

Input: list1 = [], list2 = [0]
Output: [0]
```

> 요약 두 리스트를 합처서 정렬된 리스트를 만든다.

## 접근방법

1. 리스트를 하나씩 조회해서 머지 시킨다

### 코드

> 뭔가 다른 방법이 있는듯 하다. 다른방법으로 처리 (분석이 필요)

```javascript

/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */
/**
 * @param {ListNode} list1
 * @param {ListNode} list2
 * @return {ListNode}
 */
var mergeTwoLists = function(list1, list2) {
    let prev = new ListNode();
    let prehead = prev;
    
    while (list1 != null && list2 != null) {
        if (list1.val <= list2.val) {
            prev.next = list1;
            list1 = list1.next;
        }else {
            prev.next = list2;
            list2 = list2.next;
        }
        prev = prev.next;
        console.log(prev)
    }
    
    prev.next = list1 == null ? list2 : list1
    return prehead.next;
};

```
