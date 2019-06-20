Runtime: 24 ms, faster than 99.09% of Go online submissions for Shortest Unsorted Continuous Subarray.

Memory Usage: 6.2 MB, less than 80.88% of Go online submissions for Shortest Unsorted Continuous Subarray.

```
func findUnsortedSubarray(nums []int) int {
    begin, end, m := -1, -1, 0
    for a := 1; a < len(nums); a++ {
        if nums[a] < nums[m] {
            end = a
            if begin == -1 {
                begin = a - 1
            }
            for begin > 0 && nums[begin - 1] > nums[a] {
                begin -= 1
            }       
        } else if nums[a] > nums[m] {
            m = a;
        }
    }
    if begin == -1 {
        return 0
    } else {
        return end - begin + 1
    }
}
```
