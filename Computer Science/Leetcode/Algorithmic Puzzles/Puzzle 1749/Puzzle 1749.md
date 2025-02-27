You are given an integer array `nums`. The **absolute sum** of a subarray `[numsl, numsl+1, ..., numsr-1, numsr]` is `abs(numsl + numsl+1 + ... + numsr-1 + numsr)`.

Return the **maximum** absolute sum of any **(possibly empty)** subarray of `nums`.

Note that `abs(x)` is defined as follows:

- If `x` is a negative integer, then `abs(x) = -x`.
- If `x` is a non-negative integer, then `abs(x) = x`.
 

#### Example 1:
```
Input: nums = [1,-3,2,3,-4]
Output: 5
Explanation: The subarray [2,3] has absolute sum = abs(2+3) = abs(5) = 5.
```

#### Example 2:
```
Input: nums = [2,-5,1,-4,3,-2]
Output: 8
Explanation: The subarray [-5,1,-4] has absolute sum = abs(-5+1-4) = abs(-8) = 8.
```

## **<span style="color:#38ffa9">Strategy</span>**

In [[maxcontiguoussum.pdf|Kadane's Algorithm]] we iterate over `{go} nums []int` to find the **largest subarray sum**. There we define $A = (a_{i})_{i=1}^n \subset \mathbb{Z}$ a sequence of integers and $s_0 =-\infty, t_{0}=-\infty$
$$\begin{align}
s_{j} &= \underset{}{\text{max}}\left\{  s_{j-1}+a_{j}, a_{j}  \right\}\; \tag{Current Sum} \\
t_{j} &= \underset{}{\text{max}}\; \{ t_{j-1}, s_{j} \} & \tag{Max Found Sum}
\end{align}$$

with $1 \leq j \leq n$. The key observation is, if $a_{j}$ is greater than the previous accumulated sum $s_{j-1}+a_j$, then $a_j$ itself must be a greater sum. Thus, keeping track over all maximum sums in $t_j$ finally gives the greatest sum $t_n$.

When extending the problem to finding the **largest absolute subarray sum**, the *smallest sum* can absolutely be larger than the *largest sum*, i.e.
$$\begin{align}
\widehat{s}_{j} &= \underset{}{\text{min}}\left\{  s_{j-1}+a_{j}, a_{j}  \right\} \\
\widehat{t}_{j} &= \underset{}{\text{min}}\left\{  s_{j-1}+a_{j}, a_{j}  \right\}
\end{align}$$
Finally comparing
$$out = \underset{}{\text{max}}\{ |t_{n}|, | \widehat{t}_{n}| \}\;$$
yields the desired result.

```go showLineNumbers
func maxAbsoluteSum(nums []int) int {
    
    smallSum := 0
    largeSum := 0
    maxLarge := int(-1*1e4)
    maxSmall := int(1e4)

    for _, n := range nums{
        smallSum = min(smallSum+n, n)
        largeSum = max(largeSum+n, n)
        maxSmall = min(maxSmall, smallSum)
        maxLarge = max(maxLarge, largeSum)
    } 

    return max(abs(maxSmall), abs(maxLarge))
}

func abs(num int) int{
    if num < 0{
        return -num
    }
    return num
}
```