# Middle of the Linked List
Given the head of a singly linked list, return the middle node of the linked list.

If there are two middle nodes, return the second middle node.

```text 
Example 1:


Input: head = [1,2,3,4,5]
Output: [3,4,5]
Explanation: The middle node of the list is node 3.
Example 2:


Input: head = [1,2,3,4,5,6]
Output: [4,5,6]
Explanation: Since the list has two middle nodes with values 3 and 4, we return the second one.
 

Constraints:

The number of nodes in the list is in the range [1, 100].
1 <= Node.val <= 100

```

## 접근 방법 
 * 내가 생각한 방법 
    1. 1회식 포인트를 옮겨 카운트를 구해 중간값을 구해서 미들 값을 구한다.
 * 적절한 풀이 방법 
    > Slow and Fast Point 전략을 취한다. 
    > 접접을 한칸씩, 하나는 두칸씩 하여 한번씩 순회 하여 Slow 포인트를 검출한다.

### Code 
  * 내가 생각한 방법 
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
  var middleNode = function(head) {
      let preHead = head;
      let count = 0;

      while(head !== null) {
          count++;
          head = head.next;
      }

      if (count % 2 == 0) {
          count = count / 2
      } else {
          count = count / 2 - 1
      }


      for (let i = 0; i < count; i++) {
          preHead = preHead.next;
      }

      return preHead;
  };
  ```
  * 적절한 풀이 방법
  
  ```javascript
  var middleNode = function(head) {
    slow = fast = head;
    while (fast && fast.next) {
        slow = slow.next;
        fast = fast.next.next;
    }
    return slow;
  };  
  ```
