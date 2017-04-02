https://leetcode.com/problems/valid-sudoku/#/description

36 Valid Sudoku
> 
> Determine if a Sudoku is valid, according to: Sudoku Puzzles - The Rules.
> 
> The Sudoku board could be partially filled, where empty cells are filled with the character '.'.

![image](http://upload.wikimedia.org/wikipedia/commons/thumb/f/ff/Sudoku-by-L2G-20050714.svg/250px-Sudoku-by-L2G-20050714.svg.png)

A partially filled sudoku which is valid.

Note:
A valid Sudoku board (partially filled) is not necessarily solvable. Only the filled cells need to be validated.



**分析**

这道题就是看已填充的数字是不是合法的数独就可以了，并不需要解出来。

所以思想就很简单了，就是看每一行每一列每一9宫格里有没有重复数字即可。

第 i 个九宫格里面的第 j 个元素在原矩阵的第 3*(i/3) + j/3 行，第 3*(i%3) + j%3）列 

利用HashSet的对象只能唯一可以简便查找。注意，HashSet的add()方法返回的就是boolean值


**JAVA代码**


```
    public boolean isValidSudoku(char[][] board){
        for (int i=0;i<9;i++){
            HashSet<Character> rows = new HashSet<Character>();
            HashSet<Character> colums = new HashSet<Character>();
            HashSet<Character> cube = new HashSet<Character>();
            for (int j =0;j<9;j++){
                if (board[i][j] != '.' && !rows.add(board[i][j]))
                    return false;
                if (board[j][i] != '.' && !colums.add(board[j][i]))
                    return false;
                int rowIndex = 3*(i/3);
                int colIndex = 3*(i%3);
                if (board[rowIndex+j/3][colIndex+j%3] !='.' && !cube.add(board[rowIndex+j/3][colIndex+j%3]))
                    return false;
            }
        }
        return true;
    }
```

