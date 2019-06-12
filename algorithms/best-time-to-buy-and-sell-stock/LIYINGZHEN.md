### 題目

[121. Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)

### 解題思路

出現低價就買
高價就賣
比較最大值即可

### 代碼

```go
func maxProfit(prices []int) int {
	if len(prices) == 0 {
		return 0
	}

	max := 0
	buyPrice := prices[0]

	for _, price := range prices[1:] {
		if price < buyPrice {
			buyPrice = price
		} else {
			earn := price - buyPrice
			if earn > max {
				max = earn
			}
		}
	}

	return max
}
```
