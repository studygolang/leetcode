# 二分查找


## 理论

1. 二分查找的前提条件或者基础是: 查找的元素列表是有序的
2. 当且仅当只有一个元素时结束查找


## 时间复杂度

$$
O(logn)
$$


## 算法步骤与抽象

1. 获取需要查找区间的上下限
2. 设定查找结束条件
3. 计算区间中间数
4. 将中间数与目标值比较大小，大于则取左区间，小于则取右区间
5. 不断重复3，4步骤，直到查找结束


```golang
func binarySearch(list []int, target int) (int, bool) {
	left, right := 0, len(list)

	//设定循环结束条件为：有且仅有一个元素时结束查找
	for left <= right {

		//获取中位数
		mid := (left + right) / 2

		//将中位数与给定目标数进行比较
		if target == list[mid] {
			return mid, true
		}

		//如果小于给定的目标值，则查找范围在左区间
		if list[mid] < target {
			right = mid - 1
		}

		//如果大于给定的目标值，则查找范围在右区间
		if list[mid] > target {
			left = mid + 1
		}
	}
	return 0, false
}

```



## 题目解析

#### [069-sqrtx](https://leetcode.com/problems/sqrtx/description/)

对于该题目而言，为了计算一个非负数的平方根，并且返回其整数部分。众所周知，一个非负数的平方根必定小于或者等于该数，

因此假设一个非负数为： `m`， 它的平方根为`n`， 那么就可以得到一个有序的元素列表，`[0:m]` ，接下来就可以使用二分法来求解


```golang
func mySqrt(x int) int {
    
    left, right := 1, x
    
    for left <= right {
        mid := left + (right-left) >> 1
        if mid > x / mid {
            right = mid - 1
        } else {
            left = mid + 1
        }
    }
    
    return right
}
```


#### [744-find-smallest-letter-greater-than-target](https://leetcode.com/problems/find-smallest-letter-greater-than-target/)

由于该题事先已经给出的时一个已经排序的列表，因此直接使用二分查找


```golang
func nextGreatestLetter(letters []byte, target byte) byte {
	l, m, r := 0, 0, len(letters)
	for l < r {
		m = (r + l) / 2
		if letters[m] <= target {
			l = m + 1
		} else {
			r = m
		}
	}
	return letters[l%len(letters)]
}
```


### 其他题目

- [540-single-element-in-a-sorted-array](https://leetcode.com/problems/single-element-in-a-sorted-array/description)
- [278-first-bad-version](https://leetcode.com/problems/first-bad-version/description)
- [153-find-minimum-in-rotated-sorted-array](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/description/)
- [034-find-first-and-last-position-of-element-in-sorted-array](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/description)