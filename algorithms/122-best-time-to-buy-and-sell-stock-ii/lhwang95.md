Runtime: 4 ms, faster than 96.71% of Go online submissions for Best Time to Buy and Sell Stock II.

Memory Usage: 3.1 MB, less than 54.18% of Go online submissions for Best Time to Buy and Sell Stock II.

```
func maxProfit(prices []int) int {
    b := int(^uint(0)>>1)           // 买入初值设为最大
    s := ^int(^uint(0)>>1)          // 卖出初值设为最小
    sum := 0                        // 总收益设为0
    for _, v := range prices {
        if b > v {
            b = v                   // 找到最小购入值
        }
        if s < v - b {
            s = v - b               // 找到卖出的最大收益 
        } else {
            sum += s                // 收益下降时，将前面的卖出，算入收益
            b = v                   // 重设买入初值为当前价格
            s = v - b               // 重设卖出收益为0
        }
    }
    if s > 0 {
        sum += s                    // 加上最后一天可能有的收益
    }
    return sum                      // 返回总收益
}
```
