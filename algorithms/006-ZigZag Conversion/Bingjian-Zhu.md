找规律
1.首行和最后一行算出步长
2.中间行，分别顺着找步长和逆着找步长

```golang
func convert(s string, numRows int) string {
	lenS := len(s)
	if lenS <= 2 || numRows < 2 || lenS < numRows {
		return s
	}
	res := []byte{}
	for i := 0; i < numRows; i++ {
		if i == 0 || i == numRows-1 {
			res = append(res, s[i])
			step := (numRows - 1) * 2 //步长
			for k := step + i; k < lenS; k += step {
				res = append(res, s[k])
			}
		} else {
			res = append(res, s[i])
			k := i
			for {
				//顺数第i+1行
				k += (numRows - (i + 1)) * 2 //顺数行数步长
				if k < lenS {
					res = append(res, s[k])
				} else {
					break
				}
				//逆数numRows - i行
				k += (numRows - (numRows - i)) * 2 //逆数行数步长
				if k < lenS {
					res = append(res, s[k])
				} else {
					break
				}
			}
		}
	}
	return string(res)
}
```