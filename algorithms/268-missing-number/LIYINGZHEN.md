### 題目

[268. Missing Number](https://leetcode.com/problems/missing-number/)

### 解題思路

位運算

```
a ^ a = 0
```

*例子*

nums = [0,1,3]

length = 3

```
    m   i   v     i   v     i   v
=> (3 ^ 0 ^ 0) ^ (1 ^ 1) ^ (2 ^ 3) => 2
```

### 代碼

```go
func missingNumber(nums []int) int {
	missing := len(nums)
	for i, v := range nums {
		missing = missing ^ i ^ v
	}
	return missing
}
```
