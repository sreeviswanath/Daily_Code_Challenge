##Word search problem
**Question:**  
<Given an m × n grid of characters board and a string word, return true if word exists in the grid.
The word can be constructed from letters of sequentially adjacent cells, where adjacent cells are horizontally or vertically neighboring. The same letter cell may not be used more than once.>  

**Code (Python):**
```python
def exist(board, word):
    rows = len(board)
    cols = len(board[0])

    def dfs(r, c, i):
        if i == len(word):
            return True

        if r < 0 or c < 0 or r >= rows or c >= cols or board[r][c] != word[i]:
            return False

        temp = board[r][c]
        board[r][c] = '#'

        found = (dfs(r + 1, c, i + 1) or
                 dfs(r - 1, c, i + 1) or
                 dfs(r, c + 1, i + 1) or
                 dfs(r, c - 1, i + 1))

        board[r][c] = temp

        return found

    for r in range(rows):
        for c in range(cols):
            if board[r][c] == word[0] and dfs(r, c, 0):
                return True

    return False

board = [["A","B","C","E"],["S","F","C","S"],["A","D","E","E"]]
word1 = "ABCCED"
print(exist(board, word1))

word2 = "ABCB"
print(exist(board, word2))
