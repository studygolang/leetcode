```golang
func solve(board [][]byte)  {
    
    if len(board) == 0 || len(board[0]) == 0 {
        return
    }
    
    dirx := []int{0, 0, -1, 1}
    diry := []int{-1, 1, 0, 0}
    
    var dfs func(int, int) 
    dfs = func(i, j int) {
        if i < 0 || i >= len(board) || j < 0 || j >= len(board[i]) ||
            board[i][j] == 'X' || board[i][j] == '*' {
            return
        }
        board[i][j] = '*'
        
        for k := 0; k < 4; k++ {
            dfs(i+dirx[k], j+diry[k])
        }
    }
    
    for j := 0; j < len(board[0]); j++ {
        dfs(0, j)
        dfs(len(board)-1, j)
    }
    for i := 0; i < len(board); i++ {
        dfs(i, 0)
        dfs(i, len(board[i])-1)
    }
    
    for i := range board {
        for j := range board[i] {
            if board[i][j] == '*' {
                board[i][j] = 'O'
            } else if board[i][j] == 'O' {
                board[i][j] = 'X'
            }
        }
    }
}
```
