执行用时 :0 ms
```golang
func myAtoi(str string) int {
	res := 0.0
	isNegative := false
	isBegin := false
	for i := 0; i < len(str); i++ {
		if (str[i] >= 48 && str[i] <= 57) || str[i] == 32 || str[i] == 45 || str[i] == 43 {
			if str[i] >= 48 && str[i] <= 57 { //数字
				isBegin = true
				res = res*10.0 + float64(str[i]-48)
			} else if str[i] == 45 && res <= 0 { //负号
				if isBegin {
					return checkNum(res, isNegative)
				}
				isBegin = true
				isNegative = true
			} else if str[i] == 43 { //正号
				if isBegin {
					return checkNum(res, isNegative)
				}
				isBegin = true
			} else { //空格
				if isBegin {
					return checkNum(res, isNegative)
				}
			}
		} else {
			return checkNum(res, isNegative)
		}
	}
	return checkNum(res, isNegative)
}

func checkNum(num float64, isNegative bool) int {
	if isNegative {
		num = num * -1
	}
	minVal := -math.Pow(2, 31)
	maxVal := math.Pow(2, 31) - 1
	if num < minVal {
		return int(minVal)
	} else if num > maxVal {
		return int(maxVal)
	} else {
		return int(num)
	}
}
```