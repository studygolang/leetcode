### 題目

[66. Plus One](https://leetcode.com/problems/plus-one/)

### 解題思路

這題跟 2. Add Two Numbers 有點像。
由右邊算到左邊，記得處理 carry 還有值的情況。

### 代碼

```go
func plusOne(digits []int) []int {
    length := len(digits) - 1
    right := length
    carry := 0

    for right >= 0 || carry != 0 {
        sum := 0

        // 頭進位 1
        if (right < 0 && carry != 0) {
            return append([]int{1}, digits...)
        }

        if (right == length) {
            sum = digits[right] + 1
        } else {
            sum = digits[right] + carry
        }

        digits[right] = sum % 10
        carry = sum / 10
        right--
    }

    return digits
}
```
