func romanToInt(s string) int {
	res := 0
	lenS := len(s)
	for i := 0; i < lenS; i++ {
		if s[i] == 77 { //M
			res += 1000
		} else if s[i] == 68 { //D
			res += 500
		} else if s[i] == 67 { //C

			if i < lenS-1 && s[i+1] == 68 { //CD
				res += 400
				i++
			} else if i < lenS-1 && s[i+1] == 77 { //CM
				res += 900
				i++
			} else { //C
				res += 100
			}
		} else if s[i] == 76 { //L
			res += 50
		} else if s[i] == 88 { //X
			if i < lenS-1 && s[i+1] == 76 { //XL
				res += 40
				i++
			} else if i < lenS-1 && s[i+1] == 67 { //XC
				res += 90
				i++
			} else { //X
				res += 10
			}
		} else if s[i] == 86 { //V
			res += 5
		} else if s[i] == 73 { //I
			if i < lenS-1 && s[i+1] == 86 { //IV
				res += 4
				i++
			} else if i < lenS-1 && s[i+1] == 88 { //Ix
				res += 9
				i++
			} else { //I
				res++
			}
		}
	}
	return res
}