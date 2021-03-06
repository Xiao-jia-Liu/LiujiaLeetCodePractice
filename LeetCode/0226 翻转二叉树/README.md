##### 题目描述

翻转一棵二叉树。

**示例:**

```
输入：

     4
   /   \
  2     7
 / \   / \
1   3 6   9

输出：

     4
   /   \
  7     2
 / \   / \
9   6 3   1

```

备注:
这个问题是受到 Max Howell 的 原问题 启发的 ：

谷歌：我们90％的工程师使用您编写的软件(Homebrew)，但是您却无法在面试时在白板上写出翻转二叉树这道题，这太糟糕了。



##### 题解

很简单的递归，先把根节点的左子树和右子树交换一下，然后在再递归的交换左子树的节点和右子树的节点



python版本

```python
class Solution(object):
    def invertTree(self, root):
        def invert(root):
            if root == None:
                return 0
            if root != None:
                temp = root.left
                root.left = root.right  
                root.right = temp
            invert(root.left)
            invert(root.right)
        invert(root)
        return root
```





kotlin版本

```kotlin
/**
 * Example:
 * var ti = TreeNode(5)
 * var v = ti.`val`
 * Definition for a binary tree node.
 * class TreeNode(var `val`: Int) {
 *     var left: TreeNode? = null
 *     var right: TreeNode? = null
 * }
 */
class Solution {
    fun invertTree(root: TreeNode?): TreeNode? {
        return invertInternal(root)

    }

    fun invertInternal(root: TreeNode?): TreeNode? {
        if (root == null) {
            return root
        }

        val left = root.left
        val right = root.right

        root.left = right
        root.right = left

        invertInternal(left)
        invertInternal(right)

        return root
    }
}
```



