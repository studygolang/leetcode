```golang
func twoSum(nums []int, target int) []int {
 
    var res []int
    
    finish:=false
    
    for i,v := range nums {
        diff:=target-v
        if finish {
            break
        }
        
        for j,k := range nums {
            if i==j {
                continue
            }
            if diff==k {
                finish=true
                res=append(res,i)
                res=append(res,j)
                break
            }
        }
    }
    return res
}
```