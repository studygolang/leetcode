### 485. Max Consecutive Ones
给定一个二进制数组， 计算其中最大连续1的个数。

示例 1:

输入: [1,1,0,1,1,1]
输出: 3
解释: 开头的两位和最后的三位都是连续1，所以最大连续1的个数是 3.


### 代码
```
func findMaxConsecutiveOnes(nums []int) int {
    res:=0
    left:=-1
    for i:=0;i<len(nums);i++{
        if nums[i]==1{
            res=max(res, i-left)
        }else if left<i{
            left=i
        }
    }
    return res
}

func max(a, b int)int{
    if a>b{
        return a
    }
    return b
}
```