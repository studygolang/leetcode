### 283. Move Zeroes

给定一个数组 nums，编写一个函数将所有 0 移动到数组的末尾，同时保持非零元素的相对顺序。

示例:

输入: [0,1,0,3,12]
输出: [1,3,12,0,0]
说明:

必须在原数组上操作，不能拷贝额外的数组。
尽量减少操作次数。

### 解析

当index和i都指向非0时，交换同一个元素，index和i都加1

当index和i指向0时， i加1

当index指向0，i指向非0， 交换两个元素， index和i都加1

### 代码

```go
func moveZeroes(nums []int)  {
    index:=0
    for i:=0;i<len(nums);i++{
        if nums[i]!=0{
            nums[i], nums[index]=nums[index], nums[i]
            index++
        }
    }
    
}
```

