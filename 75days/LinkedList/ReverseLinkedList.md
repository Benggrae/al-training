# Reverse Linked List

Given the head of a singly linked list, reverse the list, and return the reversed list.

``` text
Example 1:


Input: head = [1,2,3,4,5]
Output: [5,4,3,2,1]
Example 2:


Input: head = [1,2]
Output: [2,1]
Example 3:

Input: head = []
Output: []

Constraints:

The number of nodes in the list is the range [0, 5000].
-5000 <= Node.val <= 5000
```

## 생각

 1. 최종까지 가서 거꾸로 올라간다.

### code

```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */
/**
 * @param {ListNode} head
 * @return {ListNode}
 */
```

* 재귀

```javascript
    if (head.next === null) {
        console.log("head", head);
        return head;
    }
    
    let p = reverseList(head.next);
    head.next.next = head;
    head.next = null
    
    return p
```

* 반복문

```javascript

    let prev = null;
    let curr = head;
    
    while (curr != null) {
        let temp = curr.next;
        //swap 
        curr.next = prev;
        prev = curr;
        curr = temp;
    }
    return prev;
```
