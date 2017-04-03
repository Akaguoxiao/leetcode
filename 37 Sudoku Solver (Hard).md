https://leetcode.com/problems/sudoku-solver/#/description

37 Sudoku Solver

> Write a program to solve a Sudoku puzzle by filling the empty cells.
> 
> Empty cells are indicated by the character '.'.
> 
> You may assume that there will be only one unique solution.

A sudoku puzzle...

![image](http://upload.wikimedia.org/wikipedia/commons/thumb/f/ff/Sudoku-by-L2G-20050714.svg/250px-Sudoku-by-L2G-20050714.svg.png)


...and its solution numbers marked in red.

![image](http://upload.wikimedia.org/wikipedia/commons/thumb/3/31/Sudoku-by-L2G-20050714_solution.svg/250px-Sudoku-by-L2G-20050714_solution.svg.png)


**分析**

利用回溯算法，对数独中每个空格进行填数回溯，判断该数能否有解。

**JAVA代码**


```
    public void solveSudoku(char[][] board){
        if (board == null || board.length ==0)
            return;
        solve(board);
    }

    private boolean solve(char[][] board){
        //遍历数独中的每个单元格
        //遍历每一行
        for (int i =0;i<board.length;i++){
            //遍历一行的每个格子
            for (int j=0;j<board[0].length;j++){
                if (board[i][j] == '.'){
                    //从数字1到9依次计算
                    for (char c ='1';c<='9';c++){
                        //如果填入该数字，数独正确，就将此单元格填上
                        if (isValid(board,i,j,c)){
                            board[i][j] = c;
                             //最精彩的递归回溯来了。
                            if (solve(board))
                                return true;
                            else
                                board[i][j] = '.';
                        }
                    }
                    return false;
                }

            }
        }
        return true;
    }

    private boolean isValid(char[][] board,int row,int col,int c){
        for (int i=0;i<9;i++){
            if (board[i][col]!='.' && board[i][col] == c)return false;
            if (board[row][i]!='.' && board[row][i] ==c)return false;
            if (board[3*(row/3)+i/3][3*(col/3)+i%3] !='.' &&board[3*(row/3)+i/3][3*(col/3)+i%3]==c) return false;
        }
        return true;
    }

```


