---
id: depth-of-Symmetric-binary-tree
title: 二叉树的最大深度和最小深度
author: 一代风流～
author_title: To be the weirdest person
author_url: https://blog.csdn.net/qq_43176366
author_image_url: /img/cx-head.jpg

---



## 1.二叉树的最大深度

首先看下树节点的结构

```java
 public class TreeNode {
      int val;
      TreeNode left;
      TreeNode right;
      TreeNode(int x) { val = x; }
  }
```

<!--truncate-->

二叉树的最大深度比较好求 递归调用

```java
public int maxDepth(TreeNode root){
	if(root==null)
		return 0;
	if(root.left==null&&root.right==null)
		return 1;
	int leftDepth=maxDepth(root.left);
	int rightDepth=maxDepth(root.right);
	return Math.max(leftDepth,rightDepth)+1;
}

```

1.首先判断当前节点是不是空，空的话就返回0，这可以应对直接传入空树的情况。

2.如果一个节点的左孩子和右孩子都为空的话，那么这个节点就是叶子结点，返回1。

3.取左右子树的深度，返回最大深度+1，+1是对当前节点来说的。

## 2.二叉树的最小深度

二叉树的最小深度比最大深度稍微麻烦一点点，主要是左孩子或者右孩子有一个为null 的话，直接取两者中的小值的话就会变成0，需要额外的判断一下。

```java
public int minDepth(TreeNode root) {
        if(root==null)
        return 0;
        if(root.left==null&&root.right==null)
        return 1;
        
        int left=minDepth(root.left);
        int right=minDepth(root.right);
        if(left==0||right==0)
        return left+right+1;
        else{
            return Math.min(left,right)+1;
        }  
    }
```

1.和最大深度一样，判断传入空树的情况。

2.如果左右孩子都为空，则是叶子结点，返回1。

3.获取左右子树的最小深度。

4.如果左右子树有一个为空，就返回他们的和+1，因为有一方为0，其实等价于判断左子树是不是空，是的话就返回右子树的最小深度+1，判断右孩子是不是空，是的话就返回左子树的最小深度+1。

