```go
package main

import "fmt"

func main() {
	n := []int{0, 0, 1, 1, 1, 2, 2, 3, 3, 4}
	l := removeDuplicates(n)
	fmt.Println(l)
	fmt.Println(n)
}

func removeDuplicates(nums []int) int {
	l := 0
	if len(nums) == 0 {
		return l
	}
	s := nums[0:1]
	for _, v := range nums {
		if v != s[l] {
			s = append(s, v)
			l++
		}
	}
	l++
	return l
}
```