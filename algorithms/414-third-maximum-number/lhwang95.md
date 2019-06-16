Runtime: 4 ms, faster than 98.81% of Go online submissions for Third Maximum Number.

Memory Usage: 3 MB, less than 83.33% of Go online submissions for Third Maximum Number.
```
func thirdMax(nums []int) int {
    m1 := ^int(^uint(0)>>1)
    m2, m3 := m1, m1
    for _, v := range nums {
        if v == m1 || v == m2 || v == m3 {
            continue
        } else if v > m1 {
            m1, m2, m3 = v, m1, m2
        } else if v > m2 {
            m2, m3 = v, m2
        } else if v > m3 {
            m3 = v
        }
    }
    if m3 != ^int(^uint(0)>>1) {
        return m3
    } else {
        return m1
    }
}
```
