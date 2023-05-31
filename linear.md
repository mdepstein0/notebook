# Linear Algebra

This is some sample text.

---

# Optimization

(section-label)=
## Chapter 1

### Optimization Problems
Optimization problems have an **objective function** function to maximize or minimize, where the values 
that maximize or minimize the function are subject to certain **constraints**. These values are called 
**degrees of freedom**.

#### Example 1
Given a fixed Surface Area, what is the height and radius of the can with the largest area?

```{math}
A(r, h) = 2\pi r^2 + 2\pi r h \\
V(r, h) = \pi r^2 h
```

We want to $max(\pi r^2 h)$ such that $2\pi r (r + h) = $ $A_{o}$

...

#### Example 2
Drexel University professor Thomas Yu needs to make a little extra cash selling dairy products.

...

Each constraint is represented by a line with the inequality replaced with an =. We can determine 
which side of the line stasifies the constraint by picking a point that does not fall on the line
and checking it against the inequality. If it satisfies the inequality, then all the points on that
side of the line are **feasible**. Otherwise, all points on that side of the line are **infeasible**.

The set of points satisfying ALL of the constraints is known as the **feasible region**.

### Linear Programs
Example 2 from the previous section has 3 essential properites that make it a linear program:

1. It's variables are **continuous**, meaning they can take on any real value.
2. All constraints and bounds involve linear functions of the variables.
3. The objective function is *also* a linear function of the variables.

Problems with these 3 essential properties are called **Linear Programs**. 

Linear programs in **standard form** look like this: 

```{figure} lpstandardform.png
:height: 125px
:name: figure-example
```

where $z$ is your objective function, $x_{1}$...$x_{n}$ are the degrees of freedom,
and $Ax \geq b$ are the constraints. More compactly, that looks like this:

```{figure} lpsf_matricies.png
:height: 75px
:name: figure-example
```
```{figure} lpsf_equations.png
:height: 75px
:name: figure-example
```

A Linear Program always minimizes the objective function. If you have a problem where you want to
maximize the objective function, simply minimize the negative of that function. We can take this 
standard form LP and covert it to **canonical form**.

```{figure} lpcf_equations.png
:height: 75px
:name: figure-example
```

We've set $Ax = b$. In order to do that, we have to add a *slack variable* to each constraint. These
slack variables ($x_{3}$, $x_{4}$, and $x_{5}$) represent the amount by which the right-hand sides
exceed the left-hand sides. The constraints then look like this:

```{figure} lpcf_equations2.png
:height: 75px
:name: figure-example
```

And then the updated matrix forms would look like this:

```{figure} lpcf_matricies.png
:height: 75px
:name: figure-example
``` 

(section-label)=
## Chapter 2

### Jordan Exchange



(section-label)=
## Chapter 3
