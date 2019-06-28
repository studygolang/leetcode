1、方法一

Runtime: 0 ms, faster than 100.00% of Go online submissions for 1-bit and 2-bit Characters.

Memory Usage: 2.7 MB, less than 61.29% of Go online submissions for 1-bit and 2-bit Characters.
```
func isOneBitCharacter(bits []int) bool {
    i := 0
    length := len(bits)
    for i<length-1 {
        i += bits[i]+1
    }
    return i == length-1
}
```

2、方法二

Runtime: 4 ms, faster than 28.17% of Go online submissions for 1-bit and 2-bit Characters.

Memory Usage: 2.7 MB, less than 61.29% of Go online submissions for 1-bit and 2-bit Characters.
```
func isOneBitCharacter(bits []int) bool {
    flag := true
    length := len(bits)
    if length==0 || bits[length-1] != 0 {
        flag = false
    }
    for i:=0; i<length-1; {
        if bits[i]==1 && i+1 != length-1 {
            i+=2
        } else if bits[i]==0 {
            i++
        } else {
            flag = false
            break
        }
    }
    return flag
}
```
