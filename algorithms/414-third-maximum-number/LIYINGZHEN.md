### 題目

[414. Third Maximum Number](https://leetcode.com/problems/third-maximum-number/)

### 解題思路

用三個數記錄大小遍歷即可

### 代碼

```go
func thirdMax(nums []int) int {
	const INT_MAX = int(^uint(0) >> 1)
	const INT_MIN = ^INT_MAX

	s1, s2, s3 := INT_MIN, INT_MIN, INT_MIN

	for _, num := range nums {
		if num > s1 {
			s1, s2, s3 = num, s1, s2
		} else if num < s1 && num > s2 {
			s2, s3 = num, s2
		} else if num < s2 && num > s3 {
			s3 = num
		}
	}

	if s3 != INT_MIN {
        // return the third maximum number
		return s3
	} else {
        // return the maximum
		return s1
	}
}
```
