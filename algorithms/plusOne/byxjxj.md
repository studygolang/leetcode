```golang
func plusOne(digits []int) []int {
    
    carry := 1
    res := make([]int, len(digits)+1)

    for i := len(digits)-1; i >= 0; i-- {
        tmp := digits[i] + carry
        carry = tmp / 10
        res[i+1] = tmp % 10
    }

    if carry == 1 {
        res[0] = 1
    } else {
        res = res[1:]    
    }

    return res
}
```
