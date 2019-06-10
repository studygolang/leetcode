
暴力法  
这种方法应该是最容易想到的办法，利用两个for循环来遍历数组，耗时40ms。
```golang
func twoSum(nums []int, target int) []int {
    
    for i, num1 := range nums {
        tmp := target - num1
        for j, num2 := range nums {
            if j == i {
                continue
            }
            if tmp == num2 {
                return []int{i, j}
            }
        }
    }

    return nil
}
```
哈希表  
在遍历过程中，通过空间换时间，维护一个Map，记录已经存在的数字的索引，因为题目中说了 
"You may assume that each input would have exactly one solutioni"
所以并不需要考虑多个重复值的问题，只需遍历一次数组，耗时4ms。
```golang
func twoSum(nums []int, target int) []int {
    
    index := make(map[int]int)

    for i, num := range nums {
        tmp := target - num
        if j, ok := index[tmp]; ok {
            return []int{j, i}
        }

        index[tmp] = i
    }

    return nil
}
```

