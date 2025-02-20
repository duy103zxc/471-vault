

## Modularity
Be modular, that is, so that they can be divided “naturally” into coherent parts that can be separately developed and maintained
Organizational strategy: 
- objects, viewing a large system as a collection of distinct objects whose behaviors may change over time.
- The streams of information that flow in the system, much as an electrical engineer views a signal-processing system. 
### Assignment and Local State
An object is said to “have state” if its behavior is influenced by its history. *State variables*, which among them maintain enough information about history to determine the object’s current behavior

Programming without any use of assignments, as we did throughout the first two chapters of this book, is accordingly known as functional programming. 

A language that supports the concept that “equals can be substituted for equals” in an expression without changing the value of the expression is said to be referentially transparent. Referential transparency is violated when we include set! in our computer language. 

 programming that makes extensive use of assignment is known as imperative programming
### The Environment Model of Evaluation
 To apply a compound procedure to arguments, evaluate the body of the procedure with each formal parameter replaced by the corresponding argument. (Không còn đúng nữa khi áp thêm cái Assignments vào) 
 
 (in the presence of assignment, a variable can no longer be considered to be merely a name for a value. Rather, a variable must somehow designate a “place” in which values can be stored. In our new model of evaluation, these places will be maintained in structures called *environments*)
 
An environment is a sequence of *frames*. Each frame is a table (possibly empty) of *bindings*, which associate variable names with their corresponding values. (A single frame may contain at most one binding for any variable)

To evaluate a combination: 
- Evaluate the subexpressions of the combination.
- Apply the value of the operator subexpression to the values of the operand subexpressions.
The environment model of evaluation replaces the substitution model in *specifying what it means to apply a compound procedure to arguments*.


The environment model of procedure application can be summarized by two rules:
- A procedure object is applied to a set of arguments by constructing a frame, binding the formal parameters of the procedure to the arguments of the call, and then evaluating the body of the procedure in the context of the new environment constructed. The new frame has as its enclosing environment the environment part of the procedure object being applied.
- A procedure is created by evaluating a λ-expression relative to a given environment. The resulting procedure object is a pair consisting of the text of the λ-expression and a pointer to the environment in which the procedure was created. 
Evaluating the expression (set! ⟨variable⟩ ⟨value⟩) in some environment locates the binding of the variable in the environment and changes that binding to indicate the new value. 

### Frames as the Repository of Local State

### Internal Definitions

The environment model thus explains the two key properties that make local procedure definitions a useful technique for modularizing programs:

- The names of the local procedures do not interfere with names external to the enclosing procedure, because the local procedure names will be bound in the frame that the procedure creates when it is run, rather than being bound in the global environment.
- The local procedures can access the arguments of the enclosing procedure, simply by using parameter names as free variables. This is because the body of the local procedure is evaluated in an environment that is subordinate to the evaluation environment for the enclosing procedure. 

### Mutable Data
Mutable Data khác gì với Assignment đã được đề cập ở C3.1?

In order to model compound objects with changing state, we will design data abstractions to include, in addition to selectors and constructors, operations called mutators, which modify data objects. Data objects for which mutators are defined are known as mutable data objects. 
### Mutable List Structure

#### Sharing and identity