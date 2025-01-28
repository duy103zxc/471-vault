## Chương 2.4
Nó phân biệt giữa Selectors và ??

Polar vs rectangular form:
- The form z = a+bi is the rectangular form of a complex number, where (a, b) are the rectangular coordinates.
- The polar form of a complex number z = x + iy with coordinates (x, y) is given as z = r cosθ + i r sinθ = r (cosθ + i sinθ).
-> In actual computational systems, rectangular form is preferable to polar form most of the time

![[Pasted image 20250128013316.png]]
the complex number z = x + iy (where i^2 = −1) can be thought of as the point in the plane whose real coordinate is x and whose imaginary coordinate is y.


### Type tags
If both representations are included in a single system, however, we will need some way to distinguish data in polar form from data in rectangular form.

A straightforward way to accomplish this distinction is to include a type tag —the symbol rectangular or polar—as part of each complex number.

### Data-Directed Programming and Additivity

The concept of modularity is used primarily to reduce complexity by breaking a system into varying degrees of interdependence and independence across and "hide the complexity of each part behind an abstraction and interface".