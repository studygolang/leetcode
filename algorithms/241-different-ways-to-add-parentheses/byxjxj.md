```golang
func diffWaysToCompute(input string) []int {
    
    ans := make(map[string][]int)
    res := make([]int, 0, len(input))
    
    for i := range input {
        if input[i] == '+' || input[i] == '-' || input[i] == '*' {
            for _, left := range diffWaysToCompute(input[:i]) {
                for _, right := range diffWaysToCompute(input[i+1:]) {
                    res = append(res, compute(left, right, input[i]))
                }
            }
        }
    }
    
    if len(res) == 0 {
        tmp, _ := strconv.Atoi(input)
        res = append(res, tmp)
    }
    
    ans[input] = res
    
    return res
}

func compute(left, right int, op byte) int {
    switch op {
    case '+':
        return left + right
    case '-':
        return left - right
    default:
        return left * right
    } 
}
```
