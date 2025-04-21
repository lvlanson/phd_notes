---
type: [Binary Search, Prefix Sum]
---

---

You are given an integer array `nums` of length `n` and a 2D array `queries` where `queries[i] = [l_i, r_i, val_i]`.

Each `queries[i]` represents the following action on `nums`:

- Decrement the value at each index in the range `[l_i, r_i]` in `nums` by **at most** `val_i`.
- The amount by which each value is decremented can be chosen **independently** for each index.

A **Zero Array** is an array with all its elements equal to 0.

Return the **minimum** possible **non-negative** value of `k`, such that after processing the first `k` queries in **sequence**, `nums` becomes a **Zero Array**. If no such `k` exists, return -1.

**Example 1:**

**Input:** nums = \[2,0,2\], queries = \[\[0,2,1\],\[0,2,1\],\[1,1,3\]\]

**Output:** 2

**Explanation:**

- **For i = 0 (l = 0, r = 2, val = 1):**
- Decrement values at indices `[0, 1, 2]` by `[1, 0, 1]` respectively.
- The array will become `[1, 0, 1]`.
- **For i = 1 (l = 0, r = 2, val = 1):**
- Decrement values at indices `[0, 1, 2]` by `[1, 0, 1]` respectively.
- The array will become `[0, 0, 0]`, which is a Zero Array. Therefore, the minimum value of `k` is 2.

**Example 2:**

**Input:** nums = \[4,3,2,1\], queries = \[\[1,3,2\],\[0,2,1\]\]

**Output:** \-1

**Explanation:**

- **For i = 0 (l = 1, r = 3, val = 2):**
- Decrement values at indices `[1, 2, 3]` by `[2, 2, 1]` respectively.
- The array will become `[4, 1, 0, 0]`.
- **For i = 1 (l = 0, r = 2, val= 1):**
- Decrement values at indices `[0, 1, 2]` by `[1, 1, 0]` respectively.
- The array will become `[3, 0, 0, 0]`, which is not a Zero Array.

**Constraints:**

- `1 <= nums.length <= 10<sup>5</sup>`
- `0 <= nums[i] <= 5 * 10<sup>5</sup>`
- `1 <= queries.length <= 10<sup>5</sup>`
- `queries[i].length == 3`
- `0 <= l<sub>i</sub> <= r<sub>i</sub> < nums.length`
- `1 <= val<sub>i</sub> <= 5`

## Problem Explanation

Take for instance the following input
> ```nums = [3,4,5], queries=[[0,1,3],[1,2,2],[0,2,3],[1,2,1]```

Then we can determine naively by, we indicate `k` as subscript in the following example
>```
>nums_0       [ 3, 4, 5]       are all zero or below? -> no
>query_0      [-3,-3, 0]
>nums_1       [ 0, 1, 5]       are all zero or below? -> no
>query_1      [ 0,-2,-2]       
>nums_2       [ 0,-1, 3]       are all zero or below? -> no
>query_2      [-3,-3,-3]
>nums_3       [-3,-4, 0]       are all zero or below? -> yes
>							  => return k=3
>```
## **<span style="color:#38ffa9">First Naive Attempt (Failed)</span>**

```go showLineNumbers
func minZeroArray(nums []int, queries [][]int) int {
    k    := 0
    allValid := true
    for _, n := range nums{
        if n > 0{
            allValid = false
            break
        }
    }
    if allValid{
        return k
    }

    for _, q := range queries{
        allValid = true
        for i := q[0]; i <= q[1]; i++{
            nums[i] -= q[2]
            if nums[i] > 0{
                allValid = false
            }
        }
        k++
        if allValid{
            return k
        }
        
    }
    return -1
}
```

Before going into the analysis, let's define the parameters
- `len(nums)`$=n$
- `len(queries)` $=q$

First, the outer loop `{go} for _, q := range queries` over the queries has runtime $\mathcal{O}(q)$.  Embedded inside is the loop which iterates over parts of the `nums` array/slice, which are defined by `q[0] = l_i` and `q[1] = r_i` which in the worst case are of range $n$, hence the inner loop induces $\mathcal{O}(q * n)$. This attempt fails on large queries and `num` lists.

## **<span style="color:#38ffa9">Redesigned Strategy</span>**

Utilizing binary search can ease the complexity magnitude. We therefore do the following:
Consider an arbitrary list of number `nums` and some `queries`:
```
queries = [ qu_0, qu_1, qu_2, ..., qu_m, ..., qu_q ]
			 ^					    ^          ^
			left				 <-mid->     right
```
with `len(queries)`$= q$. Instead of **searching** for the minimum amount of queries iteratively, we search for it using binary search.

On top of that, instead of encoding the difference array absolutely, we use an **inverse prefix sum encoding**, i.e. let `diff` denote the **inverse prefix sum encoding** array, we define
```go showLineNumbers
diff = make([]int, len(numbers)+1, len(numbers)+1) // diff = [0, 0, ..., 0]
for _, q := range queries[:k]{ //q = [left, right, value]
	diff[q[0]]   += q[2]
	diff[q[1]+1] -= q[1]
}
```

We illustrate how this approach looks like
```
numbers = [3,4,5] | queries = [[0,1,3],[1,2,2],[0,2,1]]
step 0: diff = [ 0, 0, 0, 0]  query = [0,1,3]
		diff = [ 3, 0,-3, 0]           l r v
step 1: diff = [ 3, 0,-3, 0]  query = [1,2,2]
		diff = [ 3, 2,-3,-2]           l r v
step 2: diff = [ 3, 2,-3,-2]  query = [0,2,1]
		diff = [ 4, 2,-3,-3]
```

To yield the respective array which we subtract from `numbers`, we just add from left to right cumulatively

```
diff        = [ 4, 2, -3, -3 ]
diff_summed = [ 4, 6,  3,  0 ]
```
The last digit must always be zero, since for every query we have a value and its inverse, such that they must add to zero in the last array spot. Combining these ideas a valid solution is

```go
func minZeroArray(nums []int, queries [][]int) int {
    qLen := len(queries)
    min := 0
    max := qLen-1
    ans := -1
    allZero := true
    for _,num := range nums {
        if num != 0 {
            allZero = false
            break
        }
    }
    if allZero {
        return 0
    }
    for min<=max {
        mid := min + (max-min)/2
        if isPossible(mid,queries,nums) {
            ans = mid
            max = mid-1
        }else{
            min = mid+1
        }
    }
    if ans != -1 {
        ans++
    }
    return ans
}

func isPossible(index int,queries [][]int,nums []int) bool{
    length := len(nums)
    pos := make([]int,length+1)
    prefix := 0
    for i:=0;i<=index;i++ {
        start := queries[i][0]
        end := queries[i][1]
        val := queries[i][2]
        pos[start] += val
        pos[end+1] -= val
    }
    for i,num := range nums {
        prefix += pos[i]
        if prefix < num {
            return false
        }
    }
    return true
}
```