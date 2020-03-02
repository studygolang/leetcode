**解题思路：**
1、map统计
2、转map为切片

```go
type elem struct {
	value byte // 团队名
	rate []int // rate[i]表示该团队第i名的票数
}
```
3、排序



**代码：**

```go
func rankTeams(votes []string) string {
    tmp := make(map[byte][]int, 0)
    for i := range votes[0] {
        tmp[votes[0][i]] = make([]int, len(votes[0]))
    }
    
    for i :=0; i < len(votes[0]); i++ {
        //tmp[votes[j][i]]
        for j :=0; j < len(votes); j++ {
            tmp[votes[j][i]][i]++
        }
        
        
    }
    
    data := make([]elem,0)
    for k,v := range tmp{
        e := elem{
            value:  k,
            rate:   v,
        }
        data = append(data, e)
    }
    sort.Sort(IntSlice(data))
    var result string
    for  i:= len(data)-1; i >=0; i--  {
        result = result + string(data[i].value)
    }
    
    return result
}

type elem struct {
    value byte
    rate  []int
}
type IntSlice []elem
 
func (s IntSlice) Len() int { return len(s) }
func (s IntSlice) Swap(i, j int){ s[i], s[j] = s[j], s[i] }
func (s IntSlice) Less(i, j int) bool { 
    for K:=0; K < len(s[i].rate); K++ {
        if s[i].rate[K] != s[j].rate[K] {
            return s[i].rate[K] < s[j].rate[K]
        }
        
    }
    return s[i].value > s[j].value
}
```