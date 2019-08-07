
func moveZeroes(nums []int)  {
    var lastindexZero int =0
    for _,v:=range nums{
        if (v!=0){
            nums[lastindexZero] =v
            lastindexZero+=1
        }
    }
    for i:=lastindexZero;i<len(nums);i++ {
        nums[i]=0
    }
}
