```go
func maxProfit(prices []int) int {
    tmp := 0
	for i := 0; i < len(prices)-1; i++ {
        if prices[i] > prices[0]{
			continue
		}
		for j := i+1; j < len(prices); j++ {
			//fmt.Println(prices[j], prices[i] , "\n")
            if prices[j] < prices[i] {
				continue
			}
			tmp2 := prices[j]- prices[i]
			//fmt.Println(tmp2, "\n")
			if tmp2 > tmp {
				tmp = tmp2
			}
		}
	}
	return tmp
}
