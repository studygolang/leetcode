```golang
func pacificAtlantic(matrix [][]int) [][]int {
    
    if len(matrix) == 0 || len(matrix[0]) == 0 {
        return [][]int{}
    }
    
    visited := makeBoolSlice(len(matrix), len(matrix[0]))
    notes := makeBoolSlice(len(matrix), len(matrix[0]))
    
    pacific, atlantic := false, false
    
    dirx := []int{0, 0, -1, 1}
    diry := []int{-1, 1, 0, 0}
    
    var dfs func(int, int, int)
    dfs = func(i, j, last int)  {
        if i < 0 || j < 0 {
            pacific = true
            return 
        }
        if i >= len(matrix) || j >= len(matrix[i]) {
            atlantic = true
            return
        }
        if matrix[i][j] > last || visited[i][j] {
            return
        }
        if notes[i][j] {
            pacific, atlantic = true, true
            return
        }
        
        visited[i][j] = true
        for k := 0; k < 4; k++ {
            if pacific && atlantic {
                break
            }
            dfs(i+dirx[k], j+diry[k], matrix[i][j])
        }
        visited[i][j] = false
    }
    
    res := [][]int{}
    for i := range matrix {
        for j := range matrix[i] {
            pacific, atlantic = false, false
            dfs(i, j, matrix[i][j])
            if pacific && atlantic {
                res = append(res, []int{i, j})
                notes[i][j] = true
            }
        }
    }
    
    return res    
}

func makeBoolSlice(r, c int) [][]bool {
    res := make([][]bool, r)
    for i := range res {
        res[i] = make([]bool, c)
    }
    
    return res
}
```
