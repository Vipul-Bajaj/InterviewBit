<h1>Maximum Path in Triangle</h1>

<p>
Given a 2D integer array A of size  N * N  representing a triangle of numbers.

Find the maximum path sum from top to bottom. Each step you may move to adjacent numbers on the row below.

NOTE:

    Adjacent cells to cell (i,j) are only (i+1,j) and (i+1,j+1)
    Row i contains i integer and n-i zeroes for all i in [1,n] where zeroes represents empty cells.
Problem Constraints

    0 <= N <= 1000
    0 <= A[i][j] <= 1000
Input Format

    First and only argument is an 2D integer array A of size N * N.
Output Format
    
    Return a single integer denoting the maximum path sum from top to bottom in the triangle.
Example:

    Input 1:
        A = [
                [3, 0, 0, 0]
                [7, 4, 0, 0]
                [2, 4, 6, 0]
                [8, 5, 9, 3]
            ]
    Input 2:
        A = [
                [8, 0, 0, 0]
                [4, 4, 0, 0]
                [2, 2, 6, 0]
                [1, 1, 1, 1]
            ]
    Output 1:
        23
    Output 2:
        19
    Explanation 1:
        Given triangle looks like:  3
                                    7 4
                                    2 4 6
                                    8 5 9 3
        So max path is (3 + 7 + 4 + 9) = 23
    Explanation 2:
        Given triangle looks like:  8
                                    4 4
                                    2 2 6
                                    1 1 1 1
        So max path is (8 + 4 + 6 + 1) = 19this using only O(n) extra space, where n is the total number of rows in the triangle

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of list of integers
    # @return an integer
    def solve(self, A):
        m = len(A)
    
        if m<1:
            return 0
        
        for i in range(m-2,-1,-1):
            for j in range(len(A[i])-1):
                A[i][j] += max(A[i+1][j],A[i+1][j+1])
        
        return A[0][0]
```