涉及字符串拼接，使用bytes.Buffer
```golang
func intToRoman(num int) string {
	var res bytes.Buffer
	for num > 0 {
		if num >= 1000 {
			res.WriteString("M")
			num -= 1000
		} else if num >= 900 {
			res.WriteString("CM")
			num -= 900
		} else if num >= 500 {
			res.WriteString("D")
			num -= 500
		} else if num >= 400 {
			res.WriteString("CD")
			num -= 400
		} else if num >= 100 {
			res.WriteString("C")
			num -= 100
		} else if num >= 90 {
			res.WriteString("XC")
			num -= 90
		} else if num >= 50 {
			res.WriteString("L")
			num -= 50
		} else if num >= 40 {
			res.WriteString("XL")
			num -= 40
		} else if num >= 10 {
			res.WriteString("X")
			num -= 10
		} else if num >= 9 {
			res.WriteString("IX")
			num -= 9
		} else if num >= 5 {
			res.WriteString("V")
			num -= 5
		} else if num >= 4 {
			res.WriteString("IV")
			num -= 4
		} else if num >= 1 {
			res.WriteString("I")
			num--
		}
	}
	return res.String()
}
```