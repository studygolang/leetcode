按竖式方法求值
```golang
func multiply(num1 string, num2 string) string {
	if num1 == "0" || num2 == "0" {
		return "0"
	}
	lenNum1 := len(num1)
	lenNum2 := len(num2)
	size := lenNum1 + lenNum2
	var numRes [220][220]int
	//按乘法把各积转成二维数组
	x := 0
	for i := lenNum1 - 1; i >= 0; i-- {
		add := 0
		y := 0
		for j := lenNum2 - 1; j >= 0; j-- {
			mul := (int)(num1[i]-'0') * (int)(num2[j]-'0')
			numRes[x][size-1-y-x] = mul%10 + add
			add = mul / 10
			y++
		}
		if add > 0 {
			numRes[x][size-1-lenNum2-x] = add
		}
		x++
	}
	// for i := 0; i < size; i++ {
	// 	for j := 0; j < size; j++ {
	// 		fmt.Printf("%d  ", numRes[i][j])
	// 	}
	// 	fmt.Println()
	// }

	//把相乘的积对位相加，转成一维数组
	var res bytes.Buffer
	temp := 0
	arrNum := []int{}
	for col := size - 1; col >= 0; col-- {
		add := temp
		for row := size - 1; row >= 0; row-- {
			add += numRes[row][col]
		}
		arrNum = append(arrNum, add%10)
		temp = add / 10
	}
	// for i := 0; i < len(arrNum); i++ {
	// 	fmt.Print(arrNum[i])
	// }
	// fmt.Println()

	//把一维数组转成字符串
	isStart := false
	for i := len(arrNum) - 1; i >= 0; i-- {
		if arrNum[i] == 0 && !isStart {
			continue //去掉开头的0
		} else {
			res.WriteString(strconv.Itoa(arrNum[i]))
			isStart = true
		}
	}
	return res.String()
}
```