# [剑指 Offer 09. 用两个栈实现队列](https://leetcode-cn.com/problems/yong-liang-ge-zhan-shi-xian-dui-lie-lcof/)

## 思路：



栈的特性是后进先出，而队列的特性则是先进先出，所以，想用栈实现队列，所以需要另外一个栈的辅助，记作`stack2`。另一个栈就是存储元素的地方，记作 `stack1`

当加入一个元素的时候，直接入栈，`stack1.push(x)` 

当要从队列头部删除一个元素的时候，就需要先将 `stack1` 中除了栈底以外的元素 全部 `pop()` 出来，并放入 `stack2 ` 暂存，删除 `stack1` 栈底的元素，最后为了保持顺序，还需要将 `stack2` 中的元素再用同样的方式放回`stack1`。

## 代码如下:

```Java
class CQueue {
    
    Stack<Integer> st1,st2;
    public CQueue() {
        st1=new Stack<>();
        st2=new Stack<>();
    
    }
    
    public void appendTail(int value) {
        st1.push(value);
        
    }
    
    public int deleteHead() {
        if(st1.isEmpty()){
            return -1;
        }
        while(st1.size()>1){
            st2.push(st1.pop());
        }
        int res=st1.pop();
        while(!st2.isEmpty()){
            st1.push(st2.pop());
        }
        return res;
    }
}
```



