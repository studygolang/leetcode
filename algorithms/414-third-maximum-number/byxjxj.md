```golang
func thirdMax(nums []int) int {
    
    tmp := make([]int, 3)
    for i := range tmp {
        tmp[i] = -2<<31
    }
    
    for _, v := range nums {
        if v > tmp[0] {
            tmp[0], tmp[1], tmp[2] = v, tmp[0], tmp[1]
        } else if v > tmp[1] && v != tmp[0] {
            tmp[1], tmp[2] = v, tmp[1]
        } else if v > tmp[2] && v != tmp[0] && v != tmp[1] {
            tmp[2] = v
        }
    }
    
    if tmp[2] != -2<<31 {
        return tmp[2]
    }
       
    return tmp[0]
}
```
