1、直接调库

Runtime: 8 ms, faster than 81.87% of Go online submissions for Kth Largest Element in an Array.

Memory Usage: 3.5 MB, less than 90.45% of Go online submissions for Kth Largest Element in an Array.
```
func findKthLargest(nums []int, k int) int {
    sort.Ints(nums)
    return nums[len(nums)-k]
}
```

2、按照原理写了个堆排序，不知道什么原因速度极慢，修改了之后跟调库速度差不多…
Runtime: 8 ms, faster than 81.87% of Go online submissions for Kth Largest Element in an Array.

Memory Usage: 3.5 MB, less than 90.45% of Go online submissions for Kth Largest Element in an Array.
```
func minheap(nums []int, start int, length int) {
	var minindex, min int
    for start >= 0 {
		if 2*start + 1 < length {
			min = 2*start + 1
		}
		if 2*start + 2 < length && nums[2*start + 1] > nums[2*start + 2] {
			min = 2*start + 2
		}
		if nums[start] < nums[min] {
			min = start
		}
		start--
        if nums[minindex] > nums[min] {
            minindex = min
        }
	}
    nums[minindex], nums[0] = nums[0], nums[minindex]
}

func findKthLargest(nums []int, k int) int {
    start := k/2-1
    minheap(nums, start, k)
    for i:=k; i<len(nums); i++ {
        if nums[i] > nums[0] {
            nums[0] = nums[i]
            minheap(nums, start, k)
        }
    }
    return nums[0]
}
```
