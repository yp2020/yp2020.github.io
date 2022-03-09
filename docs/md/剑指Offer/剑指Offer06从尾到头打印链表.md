# [剑指 Offer 06. 从尾到头打印链表](https://leetcode-cn.com/problems/cong-wei-dao-tou-da-yin-lian-biao-lcof/)

## 题目描述：

输入一个链表的头节点，从尾到头反过来返回每个节点的值（用数组返回）。

## 思路：

链表只能够由前向后遍历，但是我们要求的是反向从尾到头输出，那么可以考虑用栈后进先出的特性，先将链表的元素压栈，然后再将栈中元素弹出，直到栈空为止。

## 代码：

```Java
class Solution {
    public int[] reversePrint(ListNode head) {
        Stack<Integer> stack=new Stack<>();
        ListNode p=head;
        while(p!=null){
            stack.push(p.val);
            p=p.next;
        }
        int []ans=new int [stack.size()];
        int idx=0;
        while(!stack.isEmpty()){
            ans[idx++]=stack.pop();
        }
        
        return ans;
    }
}
```

