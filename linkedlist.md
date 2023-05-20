+ [Merge Two Sorted Lists](#merge-two-sorted-lists)
+ [Reverse Linked List](#reverse-linked-list)

## Merge Two Sorted Lists

https://leetcode.com/problems/merge-two-sorted-lists/

### tried to solve without hints - success after 20 min
### Time complexity is O(len(list1)+len(list2))), for space O(2*len(list1)+len(list2))) ~ the same


<details><summary>Test Cases</summary><blockquote>
    [1,2,4] [1,3,4] -> [1,1,2,3,4,4]
    [1,2,4,5,6] [1,3,4] -> [1,1,2,3,4,4,5,6]
    [] [] -> []
   
</blockquote></details>


```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:
        cur1 = list1 # first pointer
        cur2 = list2 # second pointer
        reslisthead = ListNode() #dummy head for start
        reslist = reslisthead
        while cur1 and cur2:
            if cur1.val <= cur2.val:
                minval = cur1.val
                cur1 = cur1.next
            else:
                minval = cur2.val
                cur2 = cur2.next
            nextnode = ListNode(minval)
            reslist.next = nextnode
            reslist = reslist.next
        if cur1:
            reslist.next = cur1
        else:
            reslist.next = cur2
        return reslisthead.next
#  ПОПРОБОВАТЬ БЕЗ ИСПОЛЬЗОВАНИЯ НОВОГО СПИСКА - ЧЕРЕЗ РАСЦЕПЛЕНИЕ УКАЗАТЕЛЯ НОВОГО

```



 ## Reverse Linked List
 https://leetcode.com/problems/reverse-linked-list/
 
 ### tried to solve without hints
### Time complexity is O(len(n)), for space O(1) 

 
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        if head:
            first = head
            second = head.next
            if second:
                first.next = None
                while second.next:
                    third = second.next
                    second.next = first
                    first = second
                    second = third
                second.next = first
                return second
            else:
                return first

```
