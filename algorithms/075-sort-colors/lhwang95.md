Runtime: 0 ms, faster than 100.00% of Go online submissions for Sort Colors.

Memory Usage: 2.3 MB, less than 65.52% of Go online submissions for Sort Colors.
```
func sortColors(nums []int)  {
    color := 0
    for i:=0; i<len(nums)-1; {
        begin := i
        for nums[i] != color {
            if i == len(nums)-1 {
                color++
                i = begin
                continue
            }
            i++
            
        }
        if begin != i {
            nums[begin], nums[i] = nums[i], nums[begin]
            i = begin
        }
        for j:=i+1; j<len(nums); j++ {
            if nums[j]==color {
                i++
                nums[j], nums[i] = nums[i], nums[j]
            }
        }
        i++
        color++
    }
}
```
