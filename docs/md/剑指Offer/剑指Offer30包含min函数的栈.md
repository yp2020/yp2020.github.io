# [剑指 Offer 30. 包含min函数的栈](https://leetcode-cn.com/problems/bao-han-minhan-shu-de-zhan-lcof/)

## 题目描述

定义栈的数据结构，请在该类型中实现一个能够得到栈的最小元素的 min 函数在该栈中，调用 min、push 及 pop 的时间复杂度都是 O(1)。

## 思路

为实现得到栈的最小元素，一开始，我的想法是直接定义一个最小值并维护这个最小值，但是在调用 `pop()` 方法的时候，出现了问题，如果弹出的元素恰好是栈中的最小的元素，这个时候，单单的维护一个最小值已经解决不了这个问题了，我们可能还要维护一个第二小的值，但是也还是有问题，如果最小值被弹出，第二小的值升级成为最小值，那第二小的值如何维护呢？还是有问题。也就是说，我们得维护一系列的最小值，当最小值被弹出，剩下的最小值自动升级。那就可以用栈来实现了啊。

定义 2 个栈，一个数据栈 `stack1` 用来存储数据 ,一个辅助栈 `stack2` 用来存放栈中的一系列最小值，当元素 x 入栈 `stack1` 时，先去比较 x 与 `stack2` 栈顶元素的大小，`x <= stack2` 的栈顶元素，则 `x` 还要入栈，代表 最小值被更新。也就是说栈顶元素始终是栈中元素的最小值，当栈顶元素被弹出，栈顶指向了下面的新元素，也就是说原来第二小的元素现在变成了最小值。

## 代码

```Java
class MinStack {
   
    Stack<Integer> stack,minStack;
    /** initialize your data structure here. */
    public MinStack() {
        stack=new Stack<>();
        minStack=new Stack<>();
    }
    
    public void push(int x) {
        stack.push(x);
        if(minStack.isEmpty()||minStack.peek()>=x){
            minStack.push(x);
        }
    }
    
    public void pop() {
        int res= stack.pop();   
        if(minStack.peek()==res){
            minStack.pop();
        }
    }
    
    public int top() {
        return stack.peek();
    }
    
    public int min() {
        return minStack.peek();
    }
}
```



