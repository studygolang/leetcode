不转换成字符串的做法
```golang
func isPalindrome(x int) bool {
	if x < 0 {
		return false
	} else if x < 10 {
		return true
	} else {
		num := 0
		tmp := x
		for x > 0 {
			num = num*10 + x%10
			x = x / 10
		}
		if tmp == num {
			return true
		} else {
			return false
		}
	}
}
```