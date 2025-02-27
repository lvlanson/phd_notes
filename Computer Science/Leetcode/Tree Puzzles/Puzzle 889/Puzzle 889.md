## Construct Binary Tree from Preorder and Postorder Traversal

Given two integer arrays, `preorder` and `postorder` where `preorder` is the preorder traversal of a binary tree of distinct values and `postorder` is the postorder traversal of the same tree, reconstruct and return the binary tree.

If there exist multiple answers, you can return any of them.

#### Example 1
![[Pasted image 20250223164030.png]]

```
Input: preorder = [1,2,4,5,3,6,7], postorder = [4,5,2,6,7,3,1]
Output: [1,2,3,4,5,6,7]
```

#### Example 2

```
Input: preorder = [1], postorder = [1]
Output: [1]
```

**<h1><span style="color:#38ffa9">Strategy</span></h1>**

Recall:
>[!def] Definition Preorder
>Process all nodes of a tree by processing the root, then recursively processing all subtrees.

>[!def] Definition Postorder
>Process all nodes of a tree by recursively processing all subtrees, then finally processing the root.

>[!note] Strategy
> Note that 
> ```
> [1,2,4,5,3,6,7]
>    ^ is the first left subnode of the root 1
> ```
> and 
> ```
> [4,5,2,6,7,3,1]
>  ^ ^ ^ is the subtree spanned left to the node 
> ```
> also when ignoring all the left tree nodes and the root node
> ```
> [x,x,x,x,3,6,7]
>          ^ first appearance is root of right subtree
> ```
> which can be confirmed since 
> ```
> [x,x,x,6,7,3,x]
>        ^ ^ are its children
>```
>We treat each subarray as an own prepostorder reconstruction problem.

---

## My Solution

```go
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */
func constructFromPrePost(preorder []int, postorder []int) *TreeNode {
    baseNode := &TreeNode{
        Val: preorder[0],
    }
    if len(preorder) == 1{
        return baseNode
    }

    var postorderLeft  []int
    var postorderRight []int
    var preorderLeft   []int
    var preorderRight  []int

    for i, k := range postorder{
        if k == preorder[1]{
            postorderLeft  = postorder[:i+1]
            postorderRight = postorder[i+1:len(postorder)-1]
        }
    }

    preorderLeft  = preorder[1:len(postorderLeft)+1]
    preorderRight = preorder[len(preorderLeft)+1:]
    
    if len(preorderLeft) > 0{
        baseNode.Left  = constructFromPrePost(preorderLeft, postorderLeft)
    }
    if len(preorderRight) > 0{
        baseNode.Right = constructFromPrePost(preorderRight, postorderRight) 
    }
    
    return baseNode
}
```