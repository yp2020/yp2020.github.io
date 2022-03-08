# [剑指 Offer 24. 反转链表](https://leetcode-cn.com/problems/fan-zhuan-lian-biao-lcof/)

## 题目描述：

定义一个函数，输入一个链表的头节点，反转该链表并输出反转后链表的头节点。

## 思路：

有递归法和迭代法，这里用迭代法解决。

### 迭代法

迭代法就是 对链表进行一次遍历，然后在遍历的时候，修改节点的 `next` 指针。

时间复杂度为：`O(N)`

### 代码：

```Java
class Solution {
    public ListNode reverseList(ListNode head) {
        ListNode pre=null,cur=head;
        while(cur!=null){
            // 记录当前节点的下一个节点，
            ListNode temp=cur.next;
            // 修改当前节点的下一个节点，相当于反转链表 
            cur.next=pre;
            // 双指针前移，
            pre=cur;
            cur=temp;
        }
        return pre;
    }
}
```

### 递归法

代码很短，但是很难想出来，需要自己动手画画

时间复杂度 ,`O(N)`

### 代码：

```Java
class Solution {
    public ListNode reverseList(ListNode head) {
        if(head==null||head.next==null){
            return head;
        }
        ListNode cur=reverseList(head.next);
        head.next.next=head;
        head.next=null;
        return cur;
    }
}
```



