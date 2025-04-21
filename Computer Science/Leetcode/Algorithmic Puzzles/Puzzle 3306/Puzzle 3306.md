---
type: [Sliding Window]
---

You are given a string `word` and a **non-negative** integer `k`.

Return the total number of substrings of word that contain every vowel (`'a'`, `'e'`, `'i'`, `'o'`, and `'u'`) **at least** once and **exactly** `k` consonants.

 

#### Example 1:
```
Input: word = "aeioqq", k = 1

Output: 0
```
Explanation:

There is no substring with every vowel.

#### Example 2:
```
Input: word = "aeiou", k = 0

Output: 1
```
Explanation:

The only substring with every vowel and zero consonants is word[0..4], which is "aeiou".

#### Example 3:
```
Input: word = "ieaouqqieaouqq", k = 1

Output: 3
```
Explanation:

The substrings with every vowel and one consonant are:

`word[0..5]`, which is "ieaouq".
`word[6..11]`, which is "qieaou".
`word[7..12]`, which is "ieaouq".

## **<span style="color:#38ffa9">Strategy</span>**

We will use a **<span style="color:#38ffa9">sliding window pattern</span>**. For this we need two pointers `l` and `r` which are left and right respectively. Given we have some string `aaeXoXoiuu` then we can position `l` and `r` at the beginning of the string, i.e.
```
aaeXoXoiuu
^
l=0
r=0
```
Now we iterate over the remaining string with the right pointer `r`until we meet the condition of having all vowels in the substring

```
aaeXoXoiuu...
^       ^
l=0     r=8   
```
Note, any consecutive substring will always contain the required vowels. We only need to make sure, that the required `k` is sufficient. Let's relax the condition to instead of having **exactly** `k` consonants to having **at least** `k` consonants. We state the following condition

> `condition`: **have at least `k` consonants and at least one of each vowels**

Therefore, 
- the right pointer will move *until* we meet the `condition`
- now start shifting the left pointer as long `condition` holds
- then stop shifting the left pointer

### Illustration

Note, each time we meet the condition, we have found a set of solutions for having **at least** `k` consonants

```
aaeXoXoiuu...
^       ^----> Set of solutions for meeting minimum requirements   
```

Left Shift
>```
>aaeXoXoiuu...
>  ^      ^
>  l      r   
>```
>```
>aaeXoXoiuu...
>   ^     ^
>   l     r  
>```

Where in the last step the conditions for the left shift are violated and we return shifting right again.

### Combining at least k to exactly k

Note, that we have found at least `k` solutions and at least `k+1` solutions, we can find **exactly** `k` solutions by removing the count of `k+1` solutions from `k`.

My Solution:
```go
func countOfSubstrings(word string, k int) int64 {
    return countOfAtLeast(word, k) - countOfAtLeast(word, k + 1)
}

func vowelsMissing(vowels map[byte]int) bool{
    for _, v := range vowels{
        if v == 0{
            return true
        }
    }
    return false
}

func rightShift(vowels map[byte]int, char byte, consCount *int){
    if _, ok := vowels[char]; ok {
        vowels[char]++
    }else{
        (*consCount)++
    }
}

func leftShift(vowels map[byte]int, char byte, consCount *int){
    if _, ok := vowels[char]; ok {
        vowels[char]--
    }else{
        (*consCount)--
    }
}

func countOfAtLeast(word string, k int) int64{
    validCounter := 0
    vowels := map[byte]int{
        'a': 0,
        'e': 0,
        'i': 0,
        'o': 0,
        'u': 0,
    }
    consCount := 0
    l         := 0
    for r := 0; r < len(word); r++{
        
        rightShift(vowels, word[r], &consCount)
        for !vowelsMissing(vowels) && consCount >= k{
            validCounter += len(word) - r
            leftShift(vowels, word[l], &consCount)
            l++
        }
    }
    return int64(validCounter)
}
```

Note, my solution can still be optimized greatly.