# [剑指 Offer 58 - II. 左旋转字符串](https://leetcode-cn.com/problems/zuo-xuan-zhuan-zi-fu-chuan-lcof/)

## 题目描述：

字符串的左旋转操作是把字符串前面的若干个字符转移到字符串的尾部。请定义一个函数实现字符串左旋转操作的功能。比如，输入字符串"abcdefg"和数字2，该函数将返回左旋转两位得到的结果"cdefgab"。

## 思路：

Java 语言的话，可以采用 `StringBuilder` 进行拼接。

一次遍历字符串，先拼接后面的，也就是 第 n+1 位到末尾的字符串，后拼接前 n  位字符。最后返回即可。

## 代码：

```Java
class Solution {
    public String reverseLeftWords(String s, int n) {
        char[] str=s.toCharArray();
        StringBuilder res=new StringBuilder();
        for(int i=n;i<str.length;i++){
            res.append(str[i]);
        }
        for(int i=0;i<n;i++){
            res.append(str[i]);
        }

        return res.toString();

    }
}
```

