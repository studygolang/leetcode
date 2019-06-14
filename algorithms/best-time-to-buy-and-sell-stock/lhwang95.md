Runtime: 4 ms, faster than 98.86% of Go online submissions for Best Time to Buy and Sell Stock.

Memory Usage: 3.1 MB, less than 65.47% of Go online submissions for Best Time to Buy and Sell Stock.

```
func maxProfit(prices []int) int {
    b := int(^uint(0)>>1)           // 买入初值设为最大
    s := ^int(^uint(0)>>1)          // 卖出初值设为最小
    for _, v := range prices {
        if b > v {
            b = v                   // 找到最小购入值
        }
        if s < v - b {
            s = v - b               // 找到卖出的最大收益 
        }
    }
    if s > 0 {
        return s                    // 如果收益大于0，则购买了
    } else {
        return 0                    // 其他情况没有购买，收益为0
    }
}
```
