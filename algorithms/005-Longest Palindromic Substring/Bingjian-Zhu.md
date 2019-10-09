暴力法
```golang
func longestPalindrome(s string) string {
	lenS := len(s)
	if lenS == 1 {
		return s
	}
	maxStr := ""
	for i := 0; i < lenS; i++ {
		for j := lenS; j > i; j-- {
			tmp := s[i:j]
			if checkStr(tmp) {
				maxStr = maxString(tmp, maxStr)
			}
		}
	}
	return maxStr
}
func checkStr(s string) bool {
	lenS := len(s)
	i := 0
	j := lenS - 1
	for i < j {
		if s[i] != s[j] {
			return false
		}
		i++
		j--
	}
	return true
}

func maxString(x, y string) string {
	if len(x) < len(y) {
		return y
	}
	return x
}
```

暴力法+Go协程（不推荐，效率太比暴力法慢很多，应该是大量的字符串复制导致）
```golang
func getStr(s string, strCh chan<- string) {
	lenS := len(s)
	for i := 0; i < lenS; i++ {
		for j := lenS; j > i; j-- {
			strCh <- s[i:j]
		}
	}
	close(strCh)
}

func longestPalindrome(s string) string {
	if len(s) == 1 {
		return s
	}
	strCh := make(chan string,10)
	ch := make(chan string,10)
	maxStr := ""
	go getStr(s, strCh)
	go checkStr(strCh, ch)
	for str := range ch {
		maxStr = maxString(maxStr, str)
	}
	return maxStr
}

func checkStr(strCh <-chan string, ch chan<- string) {
	for str := range strCh {
		lenS := len(str)
		i := 0
		j := lenS - 1
		for i < j {
			if str[i] != str[j] {
				break
			}
			i++
			j--
		}
		if i >= j {
			ch <- str
		}
	}
	close(ch)
}

func maxString(x, y string) string {
	if len(x) < len(y) {
		return y
	}
	return x
}
```
马拉车算法，时间复杂度O(n)
```golang
func preProcess(s string) string {
	n := len(s)
	if n == 0 {
		return "^$"
	}
	ret := "^"
	for i := 0; i < n; i++ {
		ret += "#" + string(s[i])
	}
	ret += "#$"
	return ret

}

// 马拉车算法
func longestPalindrome(s string) string {
	T := preProcess(s)
	n := len(T)
	P := [9000]int{}
	C := 0
	R := 0
	for i := 1; i < n-1; i++ {
		i_mirror := 2*C - i
		if R > i {
			P[i] = minInt(R-i, P[i_mirror]) // 防止超出 R
		} else {
			P[i] = 0 // 等于 R 的情况
		}

		// 碰到之前讲的三种情况时候，需要利用中心扩展法
		for T[i+1+P[i]] == T[i-1-P[i]] {
			P[i]++
		}

		// 判断是否需要更新 R
		if i+P[i] > R {
			C = i
			R = i + P[i]
		}

	}

	// 找出 P 的最大值
	maxLen := 0
	centerIndex := 0
	for i := 1; i < n-1; i++ {
		if P[i] > maxLen {
			maxLen = P[i]
			centerIndex = i
		}
	}
	start := (centerIndex - maxLen) / 2 //最开始讲的求原字符串下标
	return s[start : start+maxLen]
}

func minInt(x, y int) int {
	if x < y {
		return x
	}
	return y
}
```