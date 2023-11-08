# Bisection_method-in-phyton
You can use the bisection method to find the root of the equation x^4 - x^3 + 2x^2 - 2x - 12 = 0
in the interval [-2, 0] with a tolerance of 0.0001. Here's the implementation in Python:

```python
def bisection_method(f, a, b, tolerance, max_iterations=100):
    if f(a) * f(b) >= 0:
        raise ValueError("The signs of f(a) and f(b) must be different.")
    
    iteration = 0
    while (b - a) / 2.0 > tolerance and iteration < max_iterations:
        c = (a + b) / 2.0
        if f(c) == 0:
            return round(c, 4)  # Using round() to limit decimal places
        elif f(a) * f(c) < 0:
            b = c
        else:
            a = c
        iteration += 1
        print(f"Iteration {iteration}: a = {a:.4f}, b = {b:.4f}, c = {c:.4f}, f(c) = {f(c):.6f}")
    
    return round((a + b) / 2.0, 4)

# Function for the equation x^4 - x^3 + 2x^2 - 2x - 12
def equation(x):
    return x**4 - x**3 + 2*x**2 - 2*x - 12

a = -2.0
b = 0.0
tolerance = 0.0001

root = bisection_method(equation, a, b, tolerance)
print("Root of the equation: {:.4f}".format(root))
```
Output:
```
Iteration 1: a = -2.0000, b = -1.0000, c = -1.0000, f(c) = -6.000000
Iteration 2: a = -1.5000, b = -1.0000, c = -1.5000, f(c) = 3.937500
Iteration 3: a = -1.5000, b = -1.2500, c = -1.2500, f(c) = -1.980469
Iteration 4: a = -1.3750, b = -1.2500, c = -1.3750, f(c) = 0.705322
Iteration 5: a = -1.3750, b = -1.3125, c = -1.3125, f(c) = -0.701157
Iteration 6: a = -1.3750, b = -1.3438, c = -1.3438, f(c) = -0.014388
Iteration 7: a = -1.3594, b = -1.3438, c = -1.3594, f(c) = 0.341276
Iteration 8: a = -1.3516, b = -1.3438, c = -1.3516, f(c) = 0.162406
Iteration 9: a = -1.3477, b = -1.3438, c = -1.3477, f(c) = 0.073750
Iteration 10: a = -1.3457, b = -1.3438, c = -1.3457, f(c) = 0.029617
Iteration 11: a = -1.3447, b = -1.3438, c = -1.3447, f(c) = 0.007598
Iteration 12: a = -1.3447, b = -1.3442, c = -1.3442, f(c) = -0.003399
Iteration 13: a = -1.3445, b = -1.3442, c = -1.3445, f(c) = 0.002099
Iteration 14: a = -1.3445, b = -1.3444, c = -1.3444, f(c) = -0.000650
Root of the equation: -1.3444
```
In the code above, we use the equation function to compute the value of the equation x^4 - x^3 + 2x^2 - 2x - 12
Then, we call the bisection_method with the interval [-2, 0] and a tolerance of 0.0001 to find the root of the equation. 
The root that is found is rounded to 4 decimal places as per the requested precision. 
Additionally, we have set a maximum iteration limit of 100 to ensure that the iteration stops 
if a solution is not found after a sufficiently large number of iterations.
