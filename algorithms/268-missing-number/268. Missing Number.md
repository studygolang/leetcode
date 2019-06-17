## [268. 缺失数字](https://leetcode-cn.com/problems/missing-number/)

给定一个包含 0, 1, 2, ..., n 中 n 个数的序列，找出 0 .. n 中没有出现在序列中的那个数。

示例 1:

输入: [3,0,1]
输出: 2
示例 2:

输入: [9,6,4,2,3,5,7,0,1]
输出: 8

## 思路

高斯定理:cry:

没想到



## 代码

```go
func missingNumber(nums []int) int {
    res:=0
    n:=len(nums)
    for i:=0;i<n;i++{
        res+=nums[i]
    }
    return (n+1)*n/2-res
}
```

