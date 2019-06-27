## 题目
[345. 反转字符串中的元音字母](https://leetcode-cn.com/problems/reverse-vowels-of-a-string)

## 思路
>> 思路一：双指针下标替换（效果较好）
>> 思路二：记录元音下标到数组后再替换

## 代码
>> 思路一：
```go
func reverseVowels(s string) string {
	re := strings.Split(s, "")
	s = strings.ToLower(s)
	a, b := 0, len(s)-1
	c, d := 0, 0
	for a < b {
    // 前后都满足替换
		if c==1 && d == 1{
			re[a], re[b] = re[b], re[a]
			a, b = a+1, b-1
			c, d = 0, 0
		}
		// 前面
		if  i := strings.Index("aeiou", s[a:a+1]); i != -1 && c == 0 {
			c = 1
		} else if c == 0 {
			a++
		}

		// 后面
		if i := strings.Index("aeiou", s[b:b+1]); i != -1 && d == 0  {
			d = 1
		}else if d == 0{
			b--
		}
	}

	return strings.Join(re, "")
}
```

>> 思路二
```go
func reverseVowels(s string) string {
	re := strings.Split(s, "")
	ls := []int{}
	ss := strings.ToLower(s)
	for i, v := range ss {
		if r := strings.Index("aeiou", string(v)); r != -1{
			ls = append(ls, int(i))
		}
	}
	for x,y :=0, len(ls); x<y; x,y=x+1, y-1{
		re[ls[x]], re[ls[y-1]] = re[ls[y-1]], re[ls[x]]
	}
	return strings.Join(re, "")
}
```
