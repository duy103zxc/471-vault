### The idea of composing functions.
Composing functions = to build up a function by composing one function of other functions or I guess you could think of nesting them.

![[Pasted image 20250127170334.png]]
A function is just a mapping from one set of numbers to another.
E.g: G(2) -> take the number two, input it into the function G -> get an output -> G of two.

![[Pasted image 20250127170651.png]]

Mình có thể hiểu nó một cách cơ bản là đó là một chuỗi Input và Output

### Bài tập trong phần 2
$$C(a) = 7500a - 1500$$

Trong đó:
- C = the amount of corn (in kilograms (kg))
- a = acres of land

Ví dụ: 
$$C(2) = 7500(2) - 1500= {13{,}{500}}$$
Công thức tính tiền, với **M** là lượng tiền và **c** là số kg ngô
$$M(c) = 0.9c - 50$$
Ở đây dùng hai functions liên tiếp để tính số lượng ngô, rồi mới tính lượng tiền.

**Mục tiêu**: Một function cho cả hai tác vụ ở trên

$$
\begin{aligned} M( c)&=0.9 c-50\\\\
M({{C(a)}})&=0.9({C(a)})-50\\ \\
&= 0.9({7500a-1500})-50\\\\
&= 6750a-1350-50\\\\
&=6750a-1400 \end{aligned}
$$

-> Cái này chính là **composite function**.

> Định nghĩa một cách *formal* hơn thì: 
> Given two functions, we can combine them in such a way so that the outputs of one function become the inputs of the other. This action defines a **composite function** 

