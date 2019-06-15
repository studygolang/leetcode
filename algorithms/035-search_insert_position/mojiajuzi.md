使用二分法查找相对应的元素

```go

package main

import "fmt"

func main() {
	s := []int{1, 23}
	r := searchInsert(s, 12)
	fmt.Println(r)
}

func searchInsert(nums []int, target int) int {
	min, max := 0, len(nums)-1
	for min <= max {
		if min == max && target > nums[min] {
			return min + 1
		}

		mid := (min + max) / 2
		if nums[mid] == target {
			return mid
		}

		if nums[mid] > target {
			max = mid - 1
		} else {
			min = mid + 1
		}
	}
	return min
}
```