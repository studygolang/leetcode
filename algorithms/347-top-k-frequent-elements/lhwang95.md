Runtime: 24 ms, faster than 21.30% of Go online submissions for Top K Frequent Elements.

Memory Usage: 6.1 MB, less than 81.82% of Go online submissions for Top K Frequent Elements.
```
type data struct {
    value int
    time int
}
type mp []*data

func (m mp) Len() int { 
    return len(m) 
}

func (m mp) Less(i, j int) bool { 
    return m[i].time > m[j].time 
}

func (m mp) Swap(i, j int) {
    m[i], m[j] = m[j], m[i]
}

func topKFrequent(nums []int, k int) []int {
    var dataset mp
    tempdata := make(map[int]int, 0)
    for _, v := range nums {
        if _, ok := tempdata[v]; ok {
            tempdata[v]++
        } else {
            tempdata[v] = 1
        }
    }
    for v, t := range tempdata {
        dataset = append(dataset, &data{
            value:v,
            time:t,
        })
    }
    sort.Sort(dataset)
    res := make([]int, k)
    for i:=0; i<k; i++ {
        res[i] = dataset[i].value
    }
    return res
}
```
