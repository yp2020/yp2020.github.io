# [剑指 Offer 35. 复杂链表的复制](https://leetcode-cn.com/problems/fu-za-lian-biao-de-fu-zhi-lcof/)

## 题目描述：

请实现 copyRandomList 函数，复制一个复杂链表。在复杂链表中，每个节点除了有一个 next 指针指向下一个节点，还有一个 random 指针指向链表中的任意节点或者 null

## 思路：

这题多了一个 `random`节点 ,所以需要 2次遍历链表，

因为 第一次 如果某个节点的  `random` 指针指向的节点还没创建出来，那么random 就无法正确的指向。

我们可以先把复制的节点放在原链表节点的后面，然后，等所有节点都复制完毕后，再遍历一次，进行 random 指针的指向，然后再将 2 个链表拆分开即可。

总共遍历了 三次链表，时间复杂度为 `O(N)`

## 代码：

```Java
class Solution {
    public Node copyRandomList(Node head) {
        if(head==null) return head;

        Node cur=head;
        while(cur!=null){
            Node temp=new Node(0);
            temp.val=cur.val;
            temp.next=cur.next;
            cur.next=temp;
            cur=cur.next.next;
        }

        cur=head;
    
        while(cur!=null){
            if(cur.random!=null){
                cur.next.random=cur.random.next;
            }
            cur=cur.next.next;
        }

        Node res=new Node(-1);
        Node tail=res;
        cur=head;
        while(cur!=null){
            tail.next=cur.next;
            tail=tail.next;
            cur.next=cur.next.next;
            cur=cur.next;
        }
        return res.next;
    

    }
}
```

