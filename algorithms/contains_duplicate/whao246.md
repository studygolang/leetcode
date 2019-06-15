## 217. Contains Duplicate

给定一个整数数组，判断是否存在重复元素。

如果任何值在数组中出现至少两次，函数返回 true。如果数组中每个元素都不相同，则返回 false。

示例 1:

输入: [1,2,3,1]
输出: true
示例 2:

输入: [1,2,3,4]
输出: false
示例 3:

输入: [1,1,1,3,3,4,3,2,4,2]
输出: true

## 解析

遍历数组， 如果哈希表中存在元素则返回true，  否则， 把元素加入到哈希表中

## 代码

```go
func containsDuplicate(nums []int) bool {
    // if len(nums)==0{
    //     return true
    // }
    res:=make(map[int]int)
    for i:=0;i<len(nums);i++{
        if _, ok :=res[nums[i]];ok{
            return true
        }
        res[nums[i]]++
    }
    return false
    
}
```

