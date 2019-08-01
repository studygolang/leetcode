```golang
type NumArray struct {     
    sum []int
}


func Constructor(nums []int) NumArray {
    arr := NumArray{
        sum : make([]int, len(nums)+1),
    }
    for i := range nums {
        arr.sum[i+1] = arr.sum[i] + nums[i]
    }
    
    return arr
}


func (this *NumArray) SumRange(i int, j int) int {
   return this.sum[j+1] - this.sum[i]  
}


/**
 * Your NumArray object will be instantiated and called as such:
 * obj := Constructor(nums);
 * param_1 := obj.SumRange(i,j);
 */
 ```
