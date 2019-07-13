# 763 划分字母区间

## 解法

题目定义26个小写字母，先遍历一次S，找到每个字母的最后一个位置。再遍历一遍，确保找到的每个字母的第一个位置到最后一个位置之中的字母的最后一个位置也在其中。

```golang
func partitionLabels(S string) []int {
	flag := 0
	tmp := 0
	start := -1
	last := [26]int{}
	ret := []int{}
	for i := 0; i < len(S); i++ {
		last[S[i]-'a'] = i
	}
	for i := 0; i < len(S); i++ {
		tmp = last[S[i]-'a']
		if flag < tmp {
			flag = tmp
		}
		if flag == i {
			ret = append(ret, flag-start)
			start = flag
		}
	}
	return ret
}
```