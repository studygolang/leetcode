### 345. 反转字符串中的元音字母

### 代码
```
func reverseVowels(s string) string {
	m:="aoeiuAOEIU"
	sByte := []rune(s)
	i:=0
	j:=len(s)-1
	for i<j{
		for i<j{
			if strings.ContainsRune(m, sByte[i]){
				break
			}
			i++
		}
		for i<j{
			if strings.ContainsRune(m, sByte[j]){
				break
			}
			j--
		}
		sByte[i], sByte[j]=sByte[j],sByte[i]
		i++
		j--
	}
	return string(sByte)
}
```