

# [剑指 Offer 32 - III. 从上到下打印二叉树 III](https://leetcode-cn.com/problems/cong-shang-dao-xia-da-yin-er-cha-shu-iii-lcof/)

## 题目描述：

请实现一个函数按照之字形顺序打印二叉树，即第一行按照从左到右的顺序打印，第二层按照从右到左的顺序打印，第三行再按照从左到右的顺序打印，其他行以此类推。

## 思路：

相比于上一题，这一题加入了打印顺序的要求，可以在最后特殊判断一下，进行 `reverse()`

## 代码：

```Java
class Solution {
    public List<List<Integer>> levelOrder(TreeNode root) {
        List<List<Integer>> res=new ArrayList<>();
        if(root==null){
            return res;
        }
        Queue<TreeNode> queue=new LinkedList<>();
        queue.offer(root);
        while(!queue.isEmpty()){
            List<Integer> temp=new ArrayList<>();
            int lens=queue.size();

            while(lens>0){
                TreeNode p=queue.poll();
                temp.add(p.val);
                lens--;
                if(p.left!=null){
                    queue.offer(p.left);
                }

                if(p.right!=null){
                    queue.offer(p.right);
                }
            }
            res.add(new ArrayList<>(temp));
        }

        for(int i=0;i<res.size();i++){
            if(i%2!=0){
                Collections.reverse(res.get(i));
            }
        }
        return res;
    }
}
```



