Download Link: https://assignmentchef.com/product/solved-ie523-homework-2-sudoku-solver-via-exhaustive-search-using-recursion
<br>
A <a href="https://en.wikipedia.org/wiki/Sudoku">Sudoku Puzzle</a> consists of a 9 × 9 grid, that is subdivided into nine 3 × 3 blocks. Each entry in the grid must be filled with a number from {1<em>,</em>2<em>,…,</em>9}, where some entries are already filled in. The constraints are that every number should occur exactly once in each row, each column, and each 3 × 3 block.

Write a C++ program that takes the initial board position as input and presents the solved puzzle as the output. Your program is to take the name of the input file as a command-line input, print out the initial- and final-board positions (cf. figure 4 for an illustration). The input file is formatted as follows

Figure 1: Sample output.

– there are 9 rows and 9 numbers, where the number 0 represents the unfilledvalue in the initial board. Figure 2 contains an illustrative sample.

The approach you will take for this assignment is to use recursion to implement an exhaustive-search procedure that solves a Sudoku puzzle. That is, you start with the first unfilled-value in the board and pick a valid assignment that satisfies the row-, column- and block-constraints identified above. Following this, you move to the next unfilled position and do the same. If at some point in this process you reach a partially-filled board-position that cannot be filled

9 0 0 7 0 3 5 0 4

0 0 0 0 0 0 6 7 0

0 0 6 4 5 0 8 0 0

0 1 5 2 0 0 0 6 3

0 0 0 5 0 6 0 0 0

6 7 0 0 0 9 4 5 0

0 0 8 0 4 7 2 0 0

0 4 7 0 0 0 0 0 0

3 0 9 1 0 8 0 0 5

Figure 2: Sample input file called input, which was used in the illustrative example of figure 4. The 0’s represent the incomplete board positions/values.

further under the three constraints, you backtrack to the last assignment that was made before you got stuck and modify the assigned value accordingly. This can be implemented using recursion as follows:

<em>Boolean </em><strong>Solve</strong>(row, column)

1: Find an <em>i </em>≥ row and <em>j </em>≥ column such that puzzle[i][j] = 0. If you cannot find such an <em>i </em>and <em>j</em>, then you have solved the puzzle. 2: <strong>for </strong><em>k </em>∈{1<em>,</em>2<em>,…,</em>9} <strong>do </strong>3: puzzle[i][j] = <em>k</em>.

4: <strong>if </strong>Row-, Column- and Block-Assignment constraints are satisfied by the above assignment, and <strong>Solve</strong>(<em>i</em>, <em>j</em>) returns <em>true </em><strong>then </strong>5: Return <em>true</em>.

6:               <strong>end if</strong>

7: <strong>end for</strong>

{ /* If we got here then all assignments made to puzzle[i][j] are invalid. So, we reset its value and return <em>false</em>*/}. 8: puzzle[i][j] = 0 9: Return <em>false</em>.

Figure 3: Pseudo-code for the recursive implementation of the exhaustive-search algorithm for the Sudoku puzzle. You solve the puzzle by calling <strong>Solve</strong>(0,0), assuming the indices are in the range {0<em>,</em>1<em>,…,</em>8}.

<h1>First Part of the Assignment</h1>

Your implementation should use a class Sudoku with appropriately defined private and public functions that

<ol>

 <li>check if the row-, column- and block-assignment constraints are met,</li>

 <li>reads the incomplete puzzle from an input file that is read at the commandline,</li>

 <li>prints the puzzle at any point of the search.</li>

</ol>

along with a recursive procedure that solves the puzzle that was introduced above.

<h1>Second Part of the Assignment</h1>

The following <a href="https://sandwalk.blogspot.com/2007/06/i-knew-it-there-can-be-more-than-one.html">blog</a> mentions Sudoku puzzles that can have multiple solutions. I want you to modify your code from the second programming assignment to find <em>all </em>solutions to a Sudoku puzzle.

You definitely want to be cautious with this – the empty Sudoku puzzle has theoretically 6,670,903,752,021,072,936,960 solutions. The last thing you want to do is to attempt to print them out! You will find four input files on Compass that identifies four different Sudoku puzzles. Two of them have just one solution, while the other two have multiple solutions. I suggest you run your code on these input files.

Write a C++ program that takes the initial board position as input and presents <strong>all </strong>solutions the puzzle as the output. Your program is to take the name of the input file as a command-line input, print out the initial- and finalboard positions (cf. figure 4 for an illustration). The input file format is exactly the same as what was used for the second programming assignment.

The approach you will take for this assignment is to use recursion to modify the exhaustive-search procedure that solved the Sudoku puzzle in the second programming assignment. This is a relatively straightforward thing to do, if you have understood the recursion in the previous programming assignment.

Figure 4: Sample output.