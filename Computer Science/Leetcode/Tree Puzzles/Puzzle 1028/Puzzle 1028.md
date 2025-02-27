## Recover a Tree From Preorder Traversal
[Source](https://leetcode.com/problems/recover-a-tree-from-preorder-traversal/description/)

We run a preorder depth-first search (DFS) on the `root` of a binary tree.

At each node in this traversal, we output `D` dashes (where `D` is the depth of this node), then we output the value of this node.  If the depth of a node is D, the depth of its immediate child is `D + 1`.  The depth of the `root` node is `0`.

If a node has only one child, that child is guaranteed to be the left child.

Given the output `traversal` of this traversal, recover the tree and return its `root`.

#### Example 1

![[Pasted image 20250222141803.png]]

```
Input: traversal = "1-2--3--4-5--6--7"
Output: [1,2,5,3,4,6,7]
```

#### Example 2
![[Pasted image 20250222141900.png]]

```
Input: traversal = "1-2--3---4-5--6---7"
Output: [1,2,5,3,null,6,null,4,null,7]
```

#### Example 3
![[Pasted image 20250222141928.png]]
```
Input: traversal = "1-401--349---90--88"
Output: [1,401,null,349,88,90]
```

---

### My Solution

```go
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */
import "strconv"

type Decomp struct {
    encoding string
    num      int
    level    int
}

func recoverFromPreorder(traversal string) *TreeNode {

    var decomp Decomp
    decomp.level    = -1
    decomp.encoding = traversal
    decomp.extractNum()

    added := 0
    extracted := 0
    baseNode := new(TreeNode)
    appendNode(baseNode, &decomp, 0, decomp.num, &added, &extracted)
    
    return baseNode
}

func appendNode(node *TreeNode, decomp *Decomp, currentLevel int, num int, added *int, extracted *int){
    node.Val = num
    (*added)++
    if len(decomp.encoding) == 0{
        return
    }

    decomp.extractLevel()
    decomp.extractNum()
    (*extracted)++

    if decomp.level > currentLevel{
        leftNode    := new(TreeNode)
        node.Left    = leftNode
        appendNode(leftNode, decomp, decomp.level, decomp.num, added, extracted)
    }

    if decomp.level-1 == currentLevel && (*added) <= (*extracted){
        rightNode    := new(TreeNode)
        node.Right    = rightNode
        appendNode(rightNode, decomp, decomp.level, decomp.num, added, extracted)
    }
    
}

func (decomp *Decomp) extractNum(){
    num := ""
    pos := 0
    for _, c := range decomp.encoding{
        if c == '-'{
            break
        }        
        num += string(c)
        pos++    
    }
    
    i, _ := strconv.Atoi(num)
    decomp.num = i
    decomp.encoding = decomp.encoding[pos:]
}

func (decomp *Decomp) extractLevel(){
    level := 0
    for _, c := range decomp.encoding{
        if c != '-'{
            break
        }        
        level++   
    }
    decomp.level    = level 
    decomp.encoding = decomp.encoding[level:]
}

```