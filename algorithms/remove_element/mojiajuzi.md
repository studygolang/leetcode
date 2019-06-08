```go
package main

import "fmt"

func main() {
	n := []int{0, 1, 2, 2, 3, 0, 4, 2}
	fmt.Println(n)
	l := removeElement(n, 2)
	fmt.Println(l)
	fmt.Println(n)
}
```

解题思路一

```go
func removeElement(nums []int, val int) int {

	s := nums[0:0]
	for _, v := range nums {
		if v != val {
			s = append(s, v)
		}
	}
	return len(s)
}
```



解题思路二

```go
func removeElement(nums []int, val int) int {
	l := 0
	for _, v := range nums {
		if v != val {
			nums[l] = v
			l++
		}
	}
    return l
}    
```