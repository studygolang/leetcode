```golang
func romanToInt(s string) int {
	res := 0
	lenS := len(s)
	for i := 0; i < lenS; i++ {
		if s[i] == 'M' { //M
			res += 1000
		} else if s[i] == 'D' { //D
			res += 500
		} else if s[i] == 'C' { //C

			if i < lenS-1 && s[i+1] == 'D' { //CD
				res += 400
				i++
			} else if i < lenS-1 && s[i+1] == 'M' { //CM
				res += 900
				i++
			} else { //C
				res += 100
			}
		} else if s[i] == 'L' { //L
			res += 50
		} else if s[i] == 'X' { //X
			if i < lenS-1 && s[i+1] == 'L' { //XL
				res += 40
				i++
			} else if i < lenS-1 && s[i+1] == 'C' { //XC
				res += 90
				i++
			} else { //X
				res += 10
			}
		} else if s[i] == 'V' { //V
			res += 5
		} else if s[i] == 'I' { //I
			if i < lenS-1 && s[i+1] == 'V' { //IV
				res += 4
				i++
			} else if i < lenS-1 && s[i+1] == 'X' { //IX
				res += 9
				i++
			} else { //I
				res++
			}
		}
	}
	return res
}
```