---
id: binarytrees
title: 二叉树的最近公共祖先
author: 一代风流～
author_title: To be the weirdest person
author_url: https://blog.csdn.net/qq_43176366
author_image_url: /img/cx-head.jpg


---

## 二叉树的最近公共祖先

**1.祖先的定义** ：p在root的左右子树或p==root，则称root是p的祖先。

**2.公共祖先的定义**：p，q都在root的子树上或p==root或q==root，则称root是p和q的祖先

<!--truncate-->

**3.最近公共祖先的定义**：设节点root为节点p，q的某公共祖先，若root.left和root.right都不是p，q的公共祖先，则称root是最近公共祖先。

![Picture2.png](https://pic.leetcode-cn.com/2e9f800c678fa65940262f8f355d6ecf56c693594ca0db1f8e3b266181a21b41-Picture2.png)

根据以上的定义，则只可能是以下情况之一

1. p和q在分别在root的左右子树上
2. p==root，q在root的子树上
3. q==root，p在root的子树上





```java
class Solution {
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        if(root == null || root == p || root == q) return root;
        TreeNode left = lowestCommonAncestor(root.left, p, q);
        TreeNode right = lowestCommonAncestor(root.right, p, q);
        if(left == null) return right;
        if(right == null) return left;
        return root;
    }
}
```



## 二叉搜索树的最近公共祖先

​	稍微限制下条件

1. 树为二叉搜索树
2. 树的所有节点的值都是唯一的

根据以上的条件 我们可以判断p,q,root的关系

- 若root.val<p.val,则p在root的右子树
- 若root.val>p.val,则p在root的左子树
- 若root.val==p.val,则p和root是同一节点

由此，套路为

1. 如果p，q都在root的左子树上，递归左子树
2. 如果p，q都在root的右子树上，递归右子树
3. 返回root

```java
class Solution {
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        if(root.val < p.val && root.val < q.val)
            return lowestCommonAncestor(root.right, p, q);
        if(root.val > p.val && root.val > q.val)
            return lowestCommonAncestor(root.left, p, q);
        return root;
    }
}
```









