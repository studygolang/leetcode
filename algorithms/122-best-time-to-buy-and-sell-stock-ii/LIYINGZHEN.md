### 題目

[122. Best Time to Buy and Sell Stock II](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/)

### 解題思路

這題很容易想得很複雜，原本以為要用動態規劃。

看了解答，比想象中的簡單，只要今天比昨天高就賣。

連續的在波峰波谷賣出比差值最大的波谷還賺的多。

![WechatIMG48](https://user-images.githubusercontent.com/11765228/59348805-aa8d6400-8d4a-11e9-9bf0-dc1d4fdeaf37.jpeg)


### 代碼

```go
func maxProfit(prices []int) int {
	if len(prices) == 0 {
		return 0
	}

    profit := 0
	yesterdayPrice := prices[0]

	for _, todayPrice := range prices[1:] {
		if todayPrice > yesterdayPrice {
			earn := todayPrice - yesterdayPrice
			profit += earn
		}
		yesterdayPrice = todayPrice
	}

	return profit
}
```
