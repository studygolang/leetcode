```
func plusOne(digits []int) []int {
	// 如果为空直接返回
	if digits == nil || len(digits) == 0 {
		return nil
	}
	for i := len(digits) - 1; i >= 0; i-- {
		// 最后一个<9直接返回
		if digits[i] < 9 {
			digits[i] = digits[i] + 1
			return digits
		}

		for digits[i] == 9 || digits[i] == 10 {
			// 加到index为0，在前面加一位
			if (i == 0 && digits[i] == 10) || (i == 0 && digits[i] == 9) {
				digits[i] = 0
				digits = append([]int{1}, digits[0:]...)
				return digits
			}
			// 当前数为9或10向前进一
			if digits[i] == 10 || digits[i] == 9 {
				digits[i] = 0
				digits[i - 1] = digits[i - 1] + 1
				//如果前面一个数<=9直接返回
				if digits[i - 1] <= 9 {
					return digits
				}
			}
		}
	}
	return digits
}
