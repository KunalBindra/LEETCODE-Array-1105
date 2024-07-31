# LEETCODE-Array-1105
**Explanation of the Code**

* **`dp[i]`**: Represents the minimum height to place the first `i` books.
* The outer loop iterates over each book, considering it as the last book on a shelf.
* The inner loop tries to find the optimal starting point for the current shelf, by iterating backwards from the current book.
* For each potential starting point, we calculate the maximum height and total thickness of the books on the shelf.
* If the total thickness exceeds `shelfWidth`, we break the inner loop.
* We update `dp[i+1]` with the minimum height to place the first `i+1` books, considering the current shelf arrangement.

**Dry Run**

Let's consider an example:

```
books = [[1,1], [2,3], [2,3], [1,1], [1,1], [1,1], [1,2]]
shelfWidth = 4
```

**Initialization:**

* `dp` array is initialized with `Integer.MAX_VALUE` except for `dp[0]` which is 0.

**Iteration 1 (i = 0):**
* Only one book: [[1,1]]
* `dp[1]` = 1 (minimum height to place the first book)

**Iteration 2 (i = 1):**
* Consider books [[1,1], [2,3]]
* Try placing both books on the same shelf:
  * `sumThickness` = 3 > `shelfWidth`
* Place the second book on a new shelf:
  * `dp[2]` = min(Integer.MAX_VALUE, dp[1] + 3) = 4

**Iteration 3 (i = 2):**
* Consider books [[1,1], [2,3], [2,3]]
* Try placing books 2 and 3 on the same shelf:
  * `sumThickness` = 4 <= `shelfWidth`
  * `maxHeight` = 3
  * `dp[3]` = min(Integer.MAX_VALUE, dp[1] + 3) = 4
* Try placing book 3 on a new shelf:
  * `dp[3]` = min(4, dp[2] + 3) = 4

**Continue for the remaining books...**

The final answer will be stored in `dp[n]`, where `n` is the total number of books.

**Key Points:**

* The dynamic programming approach efficiently explores all possible shelf configurations.
* The inner loop iterates backwards to find the optimal starting point for a new shelf.
* The `dp` array stores the minimum height for placing the first `i` books, allowing for efficient calculation of subsequent heights.
