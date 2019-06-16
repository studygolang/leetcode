### 題目

[35. Search Insert Position](https://leetcode.com/problems/search-insert-position/)

### 解題思路

1. 相同的話回傳當前下標
2. 小於當前值就插入到當前的位置
3. 都不對的話就塞到最後一個

### 代碼

```go
func searchInsert(nums []int, target int) int {
    for i, v := range nums {
        if (v == target) {
            return i
        }
        if (target < v) {
            return i
        }
    }

    return len(nums)
}
```
