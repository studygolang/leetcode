```golang
func exist(board [][]byte, word string) bool {
    
    if len(board) == 0 || len(board[0]) == 0 || len(word) == 0 {
        return false
    }   
    
    dirx := []int{0, 0, -1, 1}
    diry := []int{-1, 1, 0, 0}
    
    var dfs func(int, int, int) bool
    dfs = func(i, j, k int) bool {
        if i < 0 || i >= len(board) || j < 0 || j >= len(board[i]) || 
            board[i][j] != word[k] || board[i][j] == '*' {
            return false
        }
        if k == len(word)-1 {
            return true
        }
        
        res := false
        tmp := board[i][j]
        board[i][j] = '*'
        for n := 0; n < 4; n++ {
            res = res || dfs(i+dirx[n], j+diry[n], k+1)
        }
        board[i][j] = tmp
        
        return res
    }
    
    for i := range board {
        for j := range board[i] {
            if dfs(i, j , 0) {
                return true
            }
            
        }
    }
    
    return false
}
```
