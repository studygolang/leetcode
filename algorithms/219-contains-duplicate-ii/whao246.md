##  [219. 存在重复元素 II](https://leetcode-cn.com/problems/contains-duplicate-ii/)

给定一个整数数组和一个整数 k，判断数组中是否存在两个不同的索引 i 和 j，使得 nums [i] = nums [j]，并且 i 和 j 的差的绝对值最大为 k。

示例 1:

输入: nums = [1,2,3,1], k = 3
输出: true
示例 2:

输入: nums = [1,0,1,1], k = 1
输出: true
示例 3:

输入: nums = [1,2,3,1,2,3], k = 2
输出: false

## 解析

两次循环或者hash表

## 代码

#### 两次循环

耗时1784ms:cry:

```go
func containsNearbyDuplicate(nums []int, k int) bool {
    for i:=0;i<len(nums)-1;i++{
        for j:=i+1;j<len(nums);j++{
            if nums[i]==nums[j]&&abs(i-j)<=k{
                return true
            }
        }
    }
    return false
}

func abs(a int)int{
    if a<0{
        return -a
    }
    return a
}
```

#### 哈希表

耗时28ms:smile:

```Go
func containsNearbyDuplicate(nums []int, k int) bool {
    res:=make(map[int]int)
    for i:=0;i<len(nums);i++{
        _, ok:=res[nums[i]]
        if ok&&abs(i-res[nums[i]])<=k{
            return true
        }
        res[nums[i]]=i
    }
    return false
}

func abs(a int)int{
    if a<0{
        return -a
    }
    return a
}
```

