暴力法：
```golang
func maxArea(height []int) int {
	max := 0
	lenH := len(height)
	for i := 0; i < lenH; i++ {
		for j := 1; j < lenH; j++ {

			tmp := smallInt(height[j], height[i]) * (j - i)
			if tmp > max {
				max = tmp
			}
		}
	}
	return max
}
func smallInt(x, y int) int {
	if x < y {
		return x
	}
	return y
}
```

双指针方法:
```golang
func maxArea(height []int) int {
	max := 0
	i := 0
	j := len(height) - 1
	for i < j {
		tmp := smallInt(height[i], height[j]) * (j - i)
		if tmp > max {
			max = tmp
		}
		if height[i] < height[j] {
			i++
		} else {
			j--
		}
	}
	return max
}
func smallInt(x, y int) int {
	if x < y {
		return x
	}
	return y
}
```