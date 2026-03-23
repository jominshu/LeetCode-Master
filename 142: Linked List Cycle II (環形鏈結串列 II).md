[力扣题目链接](https://leetcode.com/problems/linked-list-cycle-ii/)

题意：
给定一个链表，返回链表开始入环的第一个节点。 如果链表无环，则返回 null。

为了表示给定链表中的环，使用整数 pos 来表示链表尾连接到链表中的位置（索引从 0 开始）。 如果 pos 是 -1，则在该链表中没有环。

**说明**：不允许修改给定的链表。

![循环链表](https://file1.kamacoder.com/i/algo/20200816110112704.png)

## 思路
數學證明，假設有環的情況下，從起始節點到進入環入口節點的距離為x。從入口節點到相遇節點距離為y。
從相遇節點繞回到進入節點的距離為z

快指針走的距離是慢指針的2倍
相遇時，兩指針走的距離分別為
慢指針: x+y
快指針: x+y+z+y
2(x+y) = x+2y+z
2x+2y = x+2y+z
2x=x+z
x=z

由此可知，當x=z時，我們可以利用快慢指針，慢指針從起點，快指針從相遇點，以相同速度慢慢往對方移動。
當相遇的那個節點就是題目要找的pos節點位置。

## 程式碼
```
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */

/**
 * @param {ListNode} head
 * @return {ListNode}
 */
var detectCycle = function(head) {
    // 初始化快慢指標並放在頭節點
    let slow = head;
    let fast = head;

    // 確認是否有環(快慢指標是否會相遇來判斷)
    // 確保fast跟fast.next存在
    while(fast !== null && fast.next !== null){
        // 快慢指標步數
        slow = slow.next // 慢指標走一格
        fast = fast.next.next // 快指標走兩格

        // 如果相遇了代表有環，找進入點
        if(slow === fast){
            // 把慢指針放到起點，快指針位在相遇點，同時起跑
            slow = head
            while(fast!==slow){
                slow = slow.next
                fast = fast.next
            }
            return slow
            
        }
    }
    return null;
    
};
```
