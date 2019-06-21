1、排序后比较

Runtime: 64 ms, faster than 48.60% of Go online submissions for Maximum Product of Three Numbers.

Memory Usage: 6.3 MB, less than 10.00% of Go online submissions for Maximum Product of Three Numbers.
```
func maximumProduct(nums []int) int {
    if len(nums) == 3 {
        return nums[0]*nums[1]*nums[2]
    } else {
        sort.Ints(nums)
        if nums[0]*nums[1]*nums[len(nums)-1] > nums[len(nums)-1]*nums[len(nums)-2]*nums[len(nums)-3] {
            return nums[0]*nums[1]*nums[len(nums)-1]
        } else {
            return nums[len(nums)-1]*nums[len(nums)-2]*nums[len(nums)-3]
        }
    }
}
```

2、找3个最大和2个最小的比较

Runtime: 36 ms, faster than 98.13% of Go online submissions for Maximum Product of Three Numbers.

Memory Usage: 6.3 MB, less than 76.67% of Go online submissions for Maximum Product of Three Numbers.
```
func maximumProduct(nums []int) int {
    f1, f2, z1, z2, z3 := int(^uint(0)>>1), int(^uint(0)>>1), ^int(^uint(0)>>1), ^int(^uint(0)>>1), ^int(^uint(0)>>1)
    if len(nums) == 3 {
        return nums[0]*nums[1]*nums[2]
    } else {
        for _, v := range nums {
            if v >= z1 {
                z1, z2, z3 = v, z1, z2
            } else if v >= z2 {
                z2, z3 = v, z2
            } else if v >= z3 {
                z3 = v
            }
            if v <= f1 {
                f1, f2 = v, f1
            } else if v <= f2 {
                f2 = v
            }
        }
        if z1*z2*z3 > z1*f1*f2 {
            return z1*z2*z3
        } else {
            return z1*f1*f2
        }
    }
}
```
