# Time Complexity Proof 

## Backtracking 

For COMMON-SUFFIX-LEN(n,m) (note, n in this case is whichever is smaller, n or m)
$$
R(n) = R(n - 1) + 2 \\
R(n) = an + b \\
an + b = a(n-1) + b + 2 \\
0 = -a + 2  \\
a = 2 \\ 
R(n) = 2n + b \\
\text{with base case } R(0) = 1 \implies b = 1 \\
R(n) = 2n + 1
$$

Proof for $\Theta(n)$:
$$
c_1 n \leq 2n + 1 \leq c_2 n
$$
Left Side: (pick $c_1 = 2$)
$$
2n \leq 2n + 1 \\
0 \leq 1 \\
∴ \text{True for all } n \geq 1
$$
Right Side: (pick $c_2 = 3$)
$$
2n + 1 \leq 3n \\
1 \leq n \\
∴ \text{True for all } n \geq 1
$$
Conclusion:
$$
∴ R(n) \isin \Theta(n)
$$

For the overall time complexity: (im assuming n is the bigger one)
$$
T(n, m) = nm(R(m) + 3) + 5 \\
T(n, m) = nm(m + 3) + 5 \\
T(n, m) = nm^2 + 3nm + 5
$$

Proof for $\Theta(nm^2)$:
$$
c_1 nm^2 \leq nm^2 + 3nm + 5 \leq c_2 nm^2
$$
Left Side: (pick $c_1 = 1$)
$$
1nm^2 \leq nm^2 + 3nm + 5 \\
0 \leq 3nm + 5 \\
∴ \text{True for all } n, m \geq 1
$$
Right Side: (pick $c_2 = 9$)
$$
nm^2 + 3nm + 5 \leq nm^2 + 3nm^2 + 5nm^2 = 9nm^2 \\
∴ \text{True for all } n, m \geq 1
$$
Conclusion:
$$
∴ T(n, m) \isin \Theta(nm^2)
$$

## Memoized 

For COMMON-SUFFIX-LEN(i, j): (each of the $nm$ subproblems is computed once, so any subsequent call/lookup takes $O(1)$)
$$
R(i, j) = 1 \\
∴ R(i, j) \isin \Theta(1)
$$

For the overall time complexity: (table setup + loop work + constants)
$$
T(n, m) = nm + nm(R(i, j) + 3) + 5 \\
T(n, m) = nm + nm(1 + 3) + 5 \\
T(n, m) = nm + 4nm + 5 \\
T(n, m) = 5nm + 5
$$

Proof for $\Theta(nm)$:
$$
c_1 nm \leq 5nm + 5 \leq c_2 nm
$$
Left Side: (pick $c_1 = 5$)
$$
5nm \leq 5nm + 5 \\
0 \leq 5 \\
∴ \text{True for all } n, m \geq 1
$$
Right Side: (pick $c_2 = 10$)
$$
5nm + 5 \leq 10nm \\
5 \leq 5nm \\
1 \leq nm \\
∴ \text{True for all } n, m \geq 1
$$
Conclusion:
$$
∴ T(n, m) \isin \Theta(nm)
$$

## Eager 

For the overall time complexity: (table setup + nested loops + constants)
$$
T(n, m) = nm + nm(4) + 5 \\
T(n, m) = 5nm + 5
$$

Proof for $\Theta(nm)$:
$$
c_1 nm \leq 5nm + 5 \leq c_2 nm
$$
Left Side: (pick $c_1 = 5$)
$$
5nm \leq 5nm + 5 \\
0 \leq 5 \\
∴ \text{True for all } n, m \geq 1
$$
Right Side: (pick $c_2 = 10$)
$$
5nm + 5 \leq 10nm \\
5 \leq 5nm \\
1 \leq nm \\
∴ \text{True for all } n, m \geq 1
$$
Conclusion:
$$
∴ T(n, m) \isin \Theta(nm)
$$
