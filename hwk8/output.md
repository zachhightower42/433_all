# p6
To solve this problem using dynamic programming, we can follow these steps:

1. Define the subproblems: Let's define the subproblem as finding the maximum total sale price that can be obtained by cutting a rod of length i into integer-length pieces.
    
2. Find the recurrence relation: For each rod length i, we iterate through all possible cuts j (where 1 <= j <= i) and calculate the maximum sale price that can be obtained by cutting the rod at position j and solving the subproblems for the remaining lengths. We can express this as:
    
    max_price[i]=max⁡1≤j≤i(p[j]+max_price[i−j])max_price[i]=max1≤j≤i​(p[j]+max_price[i−j])
    
    Where:
    
    - max_price[i]max_price[i] is the maximum total sale price that can be obtained by cutting a rod of length i.
    - p[j]p[j] is the sale price of a piece of length j.
    - i−ji−j represents the remaining length after the cut.
3. Initialize the base case: We initialize max_price[0]=0max_price[0]=0 since the maximum sale price of a rod of length 0 is 0.
    
4. Build the solution bottom-up: We compute the maximum total sale price for increasing rod lengths from 1 to n using the recurrence relation.
    

Here's the Python code implementing this dynamic programming algorithm:

`def max_sale_price(n, p):`
    `max_price = [0] * (n + 1)  # Initialize max_price array`

    `for i in range(1, n + 1):`
        `for j in range(1, i + 1):`
            `max_price[i] = max(max_price[i], p[j] + max_price[i - j])`

    `return max_price[n]`



`n = 5`
`prices = [0, 1, 5, 8, 9, 10]  # prices for rod lengths 0, 1, 2, 3, 4, 5`
`print("Maximum total sale price:", max_sale_price(n, prices))``

Time complexity: The time complexity of this algorithm is O(n2)O(n2) because there are two nested loops iterating over all rod lengths up to n.

Space complexity: The space complexity is O(n)O(n) since we use an array of size n+1 to store the maximum sale price for each rod length from 0 to n.



