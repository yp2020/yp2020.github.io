# [剑指 Offer 05. 替换空格](https://leetcode-cn.com/problems/ti-huan-kong-ge-lcof/)

## 题目描述：

请实现一个函数，把字符串 `s` 中的每个空格替换成"%20"。

## 思路：

在 Java 语言中 ，String 类型为不可变的数据类型。无法直接在原地修改，需要新建一个 String 来完成任务，可以使用 `StringBuilder` 来进行字符串的拼接达到目的。

由于要对整个字符串做一次遍历，所以时间复杂度为 O(N) 

## 代码：

```Java
class Solution {
    public String replaceSpace(String s) {
        
        char []str=s.toCharArray();
        StringBuilder res=new StringBuilder();
        for(int i=0;i<str.length;i++){
            if(str[i]!=' '){
                res.append(str[i]);
            }else{
                res.append("%20");
            }
        }

        return res.toString();
    }
}
```

