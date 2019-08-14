```golang
func maxAreaOfIsland(grid [][]int) int {
    
    if len(grid) == 0 || len(grid[0]) == 0 {
        return 0
    }
    
    res, cur := 0, 0
    dirx := []int{0, 0, -1, 1}
    diry := []int{-1, 1, 0, 0}
    
    var dfs func(int, int)
    dfs = func(i, j int) {
        if i < 0 || i >= len(grid) || j < 0 || j >= len(grid[i]) || grid[i][j] == 0 {
            return 
        }
        
        cur++
        grid[i][j] = 0
        for k := 0; k < 4; k++ {
            dfs(i+dirx[k], j+diry[k])
        }
    }
    
    for i := range grid {
        for j := range grid[i] {
            if grid[i][j] == 1 {
                dfs(i, j)
            }
            if cur > res {
                res = cur
            }
            cur = 0
        }
    }
    
    return res
}
```
