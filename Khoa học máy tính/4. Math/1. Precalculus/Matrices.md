Một ghi chú tổng hợp liên quan đến Ma trận

A **matrix** is a rectangular arrangement of numbers into rows and columns.
![[Pasted image 20250129023944.png]]
Đọc là *2 by 3 matrix*

A **matrix element** is simply a matrix entry. Each element in a matrix is identified by naming the row and column in which it appears.

$$
G=\left[\begin{array}{rr} 4 & 14 & -7\\ {18} & 5 & 13 \\ ~-20 & 4 & 22 \end{array}\right]
$$
In this case ‍ $g2,1 = 18$.
### Transpose
![[Pasted image 20250129031345.png]]
(Bổ sung lý thuyết sau)
### Scalars and scalar multiplication
When we work with matrices, we refer to real numbers as **scalars**.

$$
A=\left[\begin{array}{c}
10 &6 
\\\\
4& 3
\end{array}\right]
$$
-> $2A$? -> To find ‍ $2A$, simply multiply each matrix entry by 2:

$$\begin{aligned}
 2A&={2}\cdot{\left[\begin{array}{c}
10 &6 
\\\\
4& 3
\end{array}\right]}
\\\\
&={\left[\begin{array}{c}
2 \cdot10 &2\cdot 6 
\\\\
2\cdot 4& 2\cdot3
\end{array}\right]}
\\\\
&=\left[\begin{array}{c}
20 &12 
\\\\
8& 6
\end{array}\right]
\end{aligned}$$

### Adding & subtracting matrices
We can find the sum simply by *adding the corresponding entries* in matrices A and B.
$$
\begin{aligned}
 A+ B &= \left[\begin{array}{c}
{4} &{8}
\\\\
{3} & {7} 
\end{array}\right]+\left[\begin{array}{c}
{1} &{0} 
\\\\
{5} & {2} 
\end{array}\right]
\\\\
&= \left[\begin{array}{c}
{4}+{1} &{8}+{0} 
\\\\
{3}+{5} & {7}+{2} 
\end{array}\right]
\\\\
&= \left[\begin{array}{c}
5 &8  
\\\\
8 & 9 
\end{array}\right]
\end{aligned}
$$
Tương tự như subtracting

$$
\begin{aligned}
\bold C-\bold D&=\left[\begin{array}{c}
\blueE{2} &\blueE{8}  
\\\\
\blueE{0}& \blueE{9} 
\end{array}\right]-\left[\begin{array}{c}
\goldE{5} &\goldE{6} 
\\\\
\goldE{11} & \goldE{3} 
\end{array}\right]
\\\\
&=\left[\begin{array}{c}
\blueE{2}-\goldE{5} &\blueE{8}-\goldE{6}  
\\\\
\blueE{0}-\goldE{11} &\blueE{9}-\goldE{3}   
\end{array}\right]
\\\\
&=\left[\begin{array}{c}
-3 &2  
\\\\
-11 & 6 
\end{array}\right]
\end{aligned}
$$
### zero matrices
A **zero matrix** is a matrix in which all of the entries are $0$.
$$
\qquad O_{3\times 3}=\left[\begin{array}{rrr}0 & 0&0 
\\ 0 & 0&0 \\ 0 & 0&0    \end{array}\right]
$$
A zero matrix is indicated by $O$, and a subscript can be added to indicate the dimensions of the matrix if necessary.

### Dimensions considerations
$$
\begin{aligned}{\left[\begin{array}{rr}\blueD2&\blueD7 &\goldD8
\\ \blueD2& \blueD4&\goldD3
\end{array}\right]}+\left[\begin{array}{rr}{\greenD5} &\greenD2 
\\ \greenD8& \greenD1
\end{array}\right]&=\text{undefined}
\end{aligned}
$$

### Using matrices to manipulate data