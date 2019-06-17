```go
func containsDuplicate(nums []int) bool {
	re := false

	if nums == nil {
		return re
	}

	if len(nums) <= 1 {
		return re
	}

	sort.Ints(nums)
	target := nums[0]
	for i := 1; i < len(nums); i++ {
		if nums[i] == target {
			re = true
			break
		} else {
			target = nums[i]
		}
	}
	return re
}
```

借助map中的hashtab特性

```go
func containsDuplicate(nums []int) bool {
    re := false
    
    m:= make(map[int]int)
    
    for k,v := range nums {
        if _, ok := m[v]; ok {
            re = true
            break
        }else{
            m[v]=k
        }
    }
    return re
}
```