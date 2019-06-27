### 題目

[345. Reverse Vowels of a String](https://leetcode.com/problems/reverse-vowels-of-a-string/)

### 解題思路

雙指針遍歷，分別找到左右兩邊的母音然後替換即可

### 代碼

```go
func reverseVowels(s string) string {
	vowels := "aeiouAEIOU"
	left, right := 0, len(s)-1

	ss := []rune(s)

	for left < right {
		if !strings.ContainsRune(vowels, ss[left]) {
			left++
		} else if !strings.ContainsRune(vowels, ss[right]) {
			right--
		} else {
			ss[left], ss[right] = ss[right], ss[left]
			left++
			right--
		}
	}

	return string(ss)
}
```
