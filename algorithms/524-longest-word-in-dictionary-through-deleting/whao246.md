### 524. 通过删除字母匹配到字典里最长单词

### 代码

```
func findLongestWord(s string, d []string) string {
	res:=""

	for _, str:=range d{
		i:=0
		for _, c:=range s{
			if str[i]==byte(c){
				i++
			}
			if i==len(str){
				break
			}
		}
		if i == len(str) && len(str) >= len(res) {
            if len(str) > len(res) || str < res {
                    res = str;
                }
            }
	}
	return res
}
```