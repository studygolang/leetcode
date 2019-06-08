0ms,2.4Mb
```
func removeElement(nums []int, val int) int {
    head, tail := 0, len(nums)-1
    label:
    for tail >= 0 {
        for nums[tail] == val { // 从后往前遍历，找到第一个不等于val的索引
            tail--
            if (tail < 0) || (head >= tail) { // 超出索引时跳出循环
                break label
            }
        }
        if (nums[head] == val) && (head < tail) { //从前往后遍历，找到第一个等于val的索引，交换
            temp := val;
            nums[head] = nums[tail]
            nums[tail] = temp;
        }
        head++
        if head >= len(nums) { // 超出索引时跳出循环
            break
        }
    }
    if (tail >= 0 ) && (nums[tail] == val) { //预防 head==tail跳出时，该处等于val
        tail--
    } 
    return tail+1
}
```
