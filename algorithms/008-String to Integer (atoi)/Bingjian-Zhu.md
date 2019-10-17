```golang
func myAtoi(str string) int {
	res := 0.0
	isNegative := false
	isBegin := false
	for i := 0; i < len(str); i++ {
		if (str[i] >= '0' && str[i] <= '9') || str[i] == ' ' || str[i] == '-' || str[i] == '+' {
			if str[i] >= '0' && str[i] <= '9' { //数字
				isBegin = true
				res = res*10.0 + float64(str[i]-'0')
			} else if str[i] == '-' && res <= 0 { //负号
				if isBegin {
					return checkNum(res, isNegative)
				}
				isBegin = true
				isNegative = true
			} else if str[i] == '+' { //正号
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