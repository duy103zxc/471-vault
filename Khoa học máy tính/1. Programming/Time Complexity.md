
(Đến đoạn này không hiểu lắm về tính toán Time Complexity nên sẽ quay lại sau)

### Constant factor là gì?

For an overall sense of the nature of the algorithm, what counts is the N^2 part. If we double the size of the input to a program, how does that affect the running time? 

-> We use “big Theta” notation to express this sort of approximation $Θ(N^2)$

Basically that one function is always less than another function (e.g., the time for your program to run is less than $x^2$ ) except that (we don’t care about):
- constant factors (that’s what the $K$ means) => For large inputs, **the constant factor will be drowned out by the order of growth**—the exponent in the $Θ(x^i)$ notation.
- small values of x (that’s what the $N$ means) => For small inputs, your program will be **fast enough** anyway.

The algorithms you run across can be grouped into four categories according to their order of growth in time required:
- **Searching**: $Θ(N)$ time, but there are smarter algorithms that can work in $Θ(log N)$ time or even in $Θ(1)$ (that is, constant)
- **Sorting**: $Θ(N^2)$ and the clever ones are $Θ(N log N )$. 
- **Obscure problems** such as matrix multiplication, requiring $Θ(N^3)$ time.
- The **really hard problems** that require $Θ(2^N)$ or even $Θ(N!)$ time;

Giới thiệu thông qua Recursion