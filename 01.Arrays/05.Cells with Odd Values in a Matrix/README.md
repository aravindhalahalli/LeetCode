## 1252. Cells with Odd Values in a Matrix

Given n and m which are the dimensions of a matrix initialized by zeros and given an array indices where indices[i] = [ri, ci]. For each pair of [ri, ci] you have to increment all cells in row ri and column ci by 1.

Return the number of cells with odd values in the matrix after applying the increment to all indices.

 ```
Example 1:

Input: n = 2, m = 3, indices = [[0,1],[1,1]]
Output: 6
Explanation: Initial matrix = [[0,0,0],[0,0,0]].
After applying first increment it becomes [[1,2,1],[0,1,0]].
The final matrix will be [[1,3,1],[1,3,1]] which contains 6 odd numbers.

Example 2:

Input: n = 2, m = 2, indices = [[1,1],[0,0]]
Output: 0
Explanation: Final matrix = [[2,2],[2,2]]. There is no odd number in the final matrix.

```
#### Solution:
```js
/**
 * @param {number} n
 * @param {number} m
 * @param {number[][]} indices
 * @return {number}
 */
var oddCells = function(n, m, indices) {
    let finalArray = [];
    for(let i=n; i>0; i--) {
        let temp = [];
        for(let j=m; j>0; j--) {
            temp.push(0);
        }
        finalArray.push(temp);
    }
    for(let item of indices) {
        let ri = item[0];
        let ci = item[1];
        for(let [i, bit] of finalArray[ri].entries()){
            bit = bit+1
            finalArray[ri][i] = bit
        }
        for(let bit of finalArray) {
            bit[ci] += 1;
        }
    }
    let count = 0;
    for(let i=0; i<n; i++) {
        for(let j=0; j<m; j++) {
            if(finalArray[i][j]%2 !== 0) {
                count++;
            }
                
        }
    }
    return count;
};
```
