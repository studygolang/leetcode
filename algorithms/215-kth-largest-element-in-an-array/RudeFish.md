# 题目
#### [215\. 数组中的第K个最大元素](https://leetcode-cn.com/problems/kth-largest-element-in-an-array/)

# 代码
## 使用sort函数（最快的
```go
func findKthLargest(nums []int, k int) int {
	sort.Ints(nums)
	//fmt.Println()
	return nums[len(nums)-k]
}
```

##  快速排序（和sort差不多
```go
func QuickSort(left, right int, nums []int) []int  {
	l := left
	r := right
	pivot := nums[(l+r)/2]
	for l < r {
		for nums[l] > pivot{
			l++
		}
		for nums[r] < pivot {
			r--
		}

		if l >= r {
			break
		}

		nums[l], nums[r] = nums[r], nums[l]
		//fmt.Println(nums)
		if nums[l] == pivot {
			r--
		}
		if nums[r] == pivot {
			l++
		}

	}
	if l == r {
		l++
		r--
	}

	if left < r{
		QuickSort(left, r, nums)
	}
	if right > l {
		QuickSort(l, right, nums)
	}


	return nums
}

func findKthLargest(nums []int, k int)int {
	return QuickSort(0 , len(nums)-1, nums)[k-1]
}
```

## 冒泡排序
```go
func bubble_sort(nums []int) []int {
	for i:=len(nums)-1; i >=0; i-- {
		for j:=0; j<i; j++ {
			if nums[j] < nums[j+1] {
				nums[j], nums[j+1] = nums[j+1], nums[j]
			}
		}
	}
	return nums
}


func findKthLargest(nums []int, k int) int {
	sortnums:= bubble_sort(nums)
	return sortnums[k-1]
}
```

## 选择排序
```go
func findKthLargest(nums []int, k int) int {
	for j := 0; j <= len(nums)-1; j++ {
		max := nums[j]
		tag := 0
		for i:=j+1; i<len(nums); i++{
			if max < nums[i] {
				max = nums[i]
				tag = i
			}
		}
		if tag != 0 {
			nums[j], nums[tag] = nums[tag], nums[j]
			// 排到k时直接返回
			if j+1 == k {
				 return nums[k-1]
			}
		}
	}
	return nums[k-1]
}
```

## 插入排序
```go
func findKthLargest(nums []int, k int) int {
	for i:= 1; i < len(nums); i++ {
		insertNum := nums[i]
		j:=i-1
		for j>=0 && nums[j] < insertNum{
			nums[j+1] = nums[j]
			j--
		}
		if j + 1 != i{
			nums[j+1] = insertNum
		}
		// fmt.Println(nums)

	}
	return nums[k-1]
}
```
