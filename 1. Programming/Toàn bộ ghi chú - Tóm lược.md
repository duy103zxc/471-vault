Ghi chú này nhằm ghi ra những nội dung mà mình đã học được từ SICP, liệt kê theo chủ đề và sử dụng cả ghi chú từ CS61A nữa. Do khóa này mình học theo kiểu đốt cháy giai đoạn với có nhiều phần mình vẫn chưa hiểu do nó liên quan đến Calculus nên sẽ được cập nhật dần.

Có khá nhiều các chủ đề mà mình đã được học thông qua việc lập trình các ngôn ngữ khác, nhưng được trình bày một cách công phu, và cũng khó hiểu hơn nữa @@!

## Chủ đề: Functional programming
### Về Function (Hàm)
```scheme
(define (square x) (* x x)) ;; defining a function
(square 5) ;; invoking the function
(square (+ 2 3)) ;; composition with defined functions
```
Thuật ngữ: 
- The *formal parameter* is the name of the argument (x); (Khi mà viết Function thì x chính là *formal parameter*)
- The *actual argument expression* is the expression used in the invocation ((+ 2 3)); 
- The *actual argument value* is the value of the argument in the invocation (5) (Ở đây cần phân biệt giữ expression và value, expression (là một argument của Function ấy) sẽ được thực hiện trước khi chạy Function)
-> The argument’s name comes from the function’s definition; the argument’s value comes from the invocation.

A function can have any number of arguments, including zero, but must have exactly one return value. -> It’s not a function unless you always get the same answer for the same arguments.
### Normal vs. applicative order.
```scheme
> (applic (f (+ 2 3) (- 15 6))) ; show applicative-order evaluation
(f (+ 2 3) (- 15 6)) ;; applic thì sẽ đi kiểu expression -> invocation

> (normal (f (+ 2 3) (- 15 6))) ; show normal-order evaluation
(f (+ 2 3) (- 15 6)) ----> ;; normal thì sẽ đi kiểu invocation cho đến khi đạt được đến primitive operators (+, -, *, /) thì mới bắt đầu tính
(+ (g (+ 2 3)) (- 15 6))
(g (+ 2 3)) ---->

; Same result, different process.
```

-> The rule is that if you’re doing functional programming, you get **the same answer regardless of order of evaluation**.
### Higher-order procedures
> **Function as object** (that is, being able to manipulate functions as data) as opposed to the more familiar view of function as process, in which there is a sharp distinction between program and data.
#### Using functions as arguments.
```scheme
;;;;; In file cs61a/lectures/1.3/general.scm
(define pi 3.141592654)
(define (square-area r) (* r r))
(define (circle-area r) (* pi r r))
(define (sphere-area r) (* 4 pi r r))
(define (hexagon-area r) (* (sqrt 3) 1.5 r r))

;;; Có thể khái quát hóa thành
(define (area shape r) (* shape r r))

(define square 1)
(define circle pi)
(define sphere (* 4 pi))
(define hexagon (* (sqrt 3) 1.5))

;;; Và gọi kiểu này
(area square 5)

```
#### Unnamed functions.
Lambda is a special form; the formal parameter list obviously isn’t evaluated, but the body isn’t evaluated when we see the lambda, either—only when we invoke the function can we evaluate its body.
```scheme
> (sum (lambda (x) (* (sin x) (sin x))) 5 8)
2.408069916229755
```
#### First-class data types.
- the value of a variable (i.e., named)
- an argument to a function
- the return value from a function
- a member of an aggregate (Cái này là sao?)
-> Trong Scheme thì Function cũng được coi là một **First-class data type**
#### Functions as return values.
```scheme
(define (compose f g) (lambda (x) (f (g x))))
(define (twice f) (compose f f))
```
#### Let
But you should remember that let does not provide any new capabilities; it’s merely **an abbreviation for a lambda** and an invocation of the unnamed function.

```scheme
;;;;; In file cs61a/lectures/1.3/roots.scm
(define (roots a b c)
	(let ((d (sqrt (- (* b b) (* 4 a c)))))
		(se (/ (+ (- b) d) (* 2 a))
		    (/ (- (- b) d) (* 2 a)) )))
```

### Recursion and iteration

We want to know about **the efficiency of algorithms**, not of computer hardware. So instead of measuring runtime in microseconds or whatever, we ask about **the number of times some primitive (fixed-time) operation** is performed.

To estimate the efficiency of this algorithm, we can ask, **“if the argument has N numbers in it, how many multiplications do we perform?”** The answer is that we do **one multiplication for each number in the argument**, so we do N altogether. 
->The amount of time needed should roughly double if the number of numbers doubles.
```scm
;;;;; In file cs61a/lectures/1.2/growth.scm
(define (sort sent)
	(if (empty? sent)
		’()
		(insert (first sent)
				(sort (bf sent)) )))
(define (insert num sent)
	(cond ((empty? sent) (se num sent))
		((< num (first sent)) (se num sent))
		(else (se (first sent) (insert num (bf sent)))) ))
```

If there are N numbers, how many comparisons do we do?
- If there are K numbers in the argument to insert, how many comparisons does it do? K of them (Phải xử lý `insert` cho K số, không biết là "số" ở đây để chỉ số arguments hay số lượng số trong arguments =))). 
- How many times do we call insert? N times (Do có N số cần được sắp xếp)
Và mỗi lần gọi `insert` thì độ dài của `sentence` (Tức là cái `se` ấy) đều khác nhau.

(Đến đoạn này không hiểu lắm về tính toán Time Complexity nên sẽ quay lại sau)

Constant factor là gì?

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


#### The difference between a linear recursive process and an iterative process.
About memory (space) efficiency.
**linear-recursive structure**: has to keep track of N pending computations during the processing:
```scheme
during the processing:
(count ’(i want to hold your hand))
(+ 1 (count ’(want to hold your hand)))
(+ 1 (+ 1 (count ’(to hold your hand))))
(+ 1 (+ 1 (+ 1 (count ’(hold your hand)))))
(+ 1 (+ 1 (+ 1 (+ 1 (count ’(your hand))))))
(+ 1 (+ 1 (+ 1 (+ 1 (+ 1 (count ’(hand)))))))
(+ 1 (+ 1 (+ 1 (+ 1 (+ 1 (+ 1 (count ’())))))))
(+ 1 (+ 1 (+ 1 (+ 1 (+ 1 (+ 1 0))))))
(+ 1 (+ 1 (+ 1 (+ 1 (+ 1 1)))))
(+ 1 (+ 1 (+ 1 (+ 1 2))))
...

```
**iterative structure**: does not need extra memory to remember all the unfinished tasks during the computation
```scheme
(count ’(i want to hold your hand))
(iter ’(i want to hold your hand) 0)
(iter ’(want to hold your hand) 1)
(iter ’(to hold your hand) 2)
(iter ’(hold your hand) 3)
(iter ’(your hand) 4)
(iter ’(hand) 5)
(iter ’() 6)
6
```

> For the purposes of **this course** (CS61A), you should generally use the simpler linear-recursive structure and not try for the more complicated iterative structure; the efficiency saving is not worth the increased complexity.

#### More is less: non-obvious efficiency improvements.
Trong phần này thì có hai ví dụ (Đọc ghi chú tuần 3 của CS61A), ví dụ đầu tiên thì đơn giản nhưng time complexity lên tới $Θ(2^n)$ nhưng chương trình số 2 phức tạp hơn nhiều, nhưng chỉ sử dụng: $Θ(n^2)$
**Moral**: When it really matters, think hard about your algorithm instead of trying to fine-tune a few microseconds off the obvious algorithm


## Data abstraction, sequences
### Big ideas: data abstraction, abstraction barrier.
If we are dealing with some particular type of data, we want to talk about it in terms of **its meaning**, **not** in terms of **how it happens to be represented** in the computer.
```scheme
(define (total hand)
	(if (empty? hand)
		0
		(+ (rank (one-card hand))
			(total (remaining-cards hand)) )))
(define rank butlast)
(define suit last)

(define one-card last)
(define remaining-cards butlast)
```
The auxiliary functions like *rank* are called **selectors** because they select one component of a multi-part *datum* (a single piece of information).

Actually we’re *violating* the data abstraction when typing ’(3h 10c 4d) -> knowing how the cards are represented. Hiding the representation, we need **constructor** functions as well as the *selectors*:

```scheme
;;;;; In file cs61a/lectures/2.1/total.scm
(define (make-card rank suit)
	(word rank (first suit)) )
(define make-hand se)

> (total (make-hand (make-card 3 ’heart)
					(make-card 10 ’club)
					(make-card 4 ’diamond) 
					))

17
```

> Using data abstraction we can **change the implementation of the data type without affecting the programs** that use that data type.

You can write programs using *sentences* (Ở đây chỉ kiểu dữ liệu được cung cấp bởi CS61A) without knowing how they’re implemented. But it turns out that because of the way they are implemented, `first` and `butfirst` take $Θ(1)$ time, while `last` and `butlast` take $Θ(N)$ time. 
-> If you know that, your programs will be faster (Biết cách implementation giúp bạn hiểu bạn đang làm cái gì =D)
### Pairs