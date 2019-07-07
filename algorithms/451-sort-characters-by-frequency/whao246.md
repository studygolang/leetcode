###  451. 根据字符出现频率排序
### 代码

```
func frequencySort(s string) string{
    m:=make(map[byte]int)
    out:=[]int{}
    res:=[]byte{}
    for i:=0;i<len(s);i++{
        m[s[i]]++
    }
    for _, v:=range m{
        out=append(out, v)
    }
    sort.Ints(out)
    for i:=0;i<len(out);i++{
        for k, v:=range m{
            if out[len(out)-i-1]==v{
                for j:=0;j<v;j++{
                    res=append(res, k)
                }
            }    
        }
    
    }
    return string(res)
}

```