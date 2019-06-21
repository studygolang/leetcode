### 題目

[628. Maximum Product of Three Numbers](https://leetcode.com/problems/maximum-product-of-three-numbers/)

### 解題思路

注意負數。

找出前 3 大，與前 2 小數字，比較乘積。

### 代碼

```go
import "math"

func maximumProduct(nums []int) int {
	min1, min2 := math.MaxInt32, math.MaxInt32
	max1, max2, max3 := -math.MaxInt32, -math.MaxInt32, -math.MaxInt32

	for _, v := range nums {
        // 找出前 3 大數字
		if v > max1 {
			max3 = max2
			max2 = max1
			max1 = v
		} else if v > max2 {
			max3 = max2
			max2 = v
		} else if v > max3 {
			max3 = v
        }

        // 找出前 2 小數字
		if v < min1 {
			min2 = min1
			min1 = v
		} else if v < min2 {
			min2 = v
		}
	}

	if max1*max2*max3 > max1*min1*min2 {
		return max1 * max2 * max3
	}
	return max1 * min1 * min2
}
```
