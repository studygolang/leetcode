0ms,2.4Mb
题目要求不能增加空间，用append之类的截取在底层上不确定会不会申请新的空间
结合使用案例，直接操作列表，将前面等于val的和后面不等的互换，最后返回从起始到最后一个不是val那部分的长度
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
