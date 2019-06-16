Runtime: 4 ms, faster than 98.79% of Go online submissions for Two Sum II - Input array is sorted.

Memory Usage: 3 MB, less than 70.90% of Go online submissions for Two Sum II - Input array is sorted.


```
func twoSum(numbers []int, target int) []int {
    data := make(map[int]int)

	for i, v := range numbers {
		rest := target - v

		restIndex, ok := data[rest]
		if ok {
            if i > restIndex {
                return []int{restIndex+1, i+1}
            } else {
                return []int{i+1, restIndex+1}
            }
		}
		data[v] = i
	}

	return nil
}
```
