### 414. Third Maximum Number

给定一个非空数组，返回此数组中第三大的数。如果不存在，则返回数组中最大的数。要求算法时间复杂度必须是O(n)。

示例 1:

输入: [3, 2, 1]

输出: 1

解释: 第三大的数是 1.
示例 2:

输入: [1, 2]

输出: 2

解释: 第三大的数不存在, 所以返回最大的数 2 .
示例 3:

输入: [2, 2, 3, 1]

输出: 1

解释: 注意，要求返回第三大的数，是指第三大且唯一出现的数。
存在两个值为2的数，它们都排第二。

### 解析

```go
func thirdMax(nums []int) int {
    first:=-1<<32
    second:=-1<<32
    third:=-1<<32
    for i:=0;i<len(nums);i++{
        if nums[i]>first{
            third=second
            second=first
            first=nums[i]
        }else if nums[i]<first&&nums[i]>second{
            third=second
            second=nums[i]
        }else if nums[i]<second&&nums[i]>third{
            third=nums[i]
        }
    }
    if third==-1<<32{
        return first
    }else{
        return third
    }  
}
```

