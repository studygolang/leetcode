```golang
type NumArray struct {     
    sum []int
}


func Constructor(nums []int) NumArray {
    arr := NumArray{
        sum : make([]int, len(nums)),
    }
    for i := range nums {
        if i == 0 {
            arr.sum[i] = nums[i]
        } else {
            arr.sum[i] = arr.sum[i-1] + nums[i]
        }
    }
    
    return arr
}


func (this *NumArray) SumRange(i int, j int) int {
    if i == 0 || j == 0 {
        return this.sum[j]
    }
   return this.sum[j] - this.sum[i-1]  
}


/**
 * Your NumArray object will be instantiated and called as such:
 * obj := Constructor(nums);
 * param_1 := obj.SumRange(i,j);
 */
 ```
