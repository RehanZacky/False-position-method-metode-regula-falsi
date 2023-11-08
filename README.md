# Bisection_method-in-phyton
Here's the Python code that uses the False Position (Regula Falsi) method to find the root of the equation f(x) = x^2 - 6x + 5 = 0 and records each iteration in a table:

```python
def f(x):
    return x**2 - 6*x + 5

def false_position(a, b, tol, max_iterations):
    iteration = 0
    results = []

    while iteration < max_iterations:
        c = (a * f(b) - b * f(a)) / (f(b) - f(a))
        f_c = f(c)
        results.append((iteration + 1, a, b, c, f(a), f(b), f_c))

        if f_c == 0 or (b - a) < tol:
            break
        elif f_c * f(a) < 0:
            b = c
        else:
            a = c

        iteration += 1

    return c, results

a = 3.0
b = 6.0
tolerance = 0.001  # Tolerance to 3 decimal places
max_iterations = 7  # Maximum number of iterations

root, table = false_position(a, b, tolerance, max_iterations)

print("| Iteration |   a   |   b   |   c   |  f(a)  |  f(b) |  f(c)  |")
print("|-----------|-------|-------|-------|--------|-------|--------|")
for row in table:
    print("|     {}     | {:.3f} | {:.3f} | {:.3f} | {:.3f} | {:.3f} | {:.3f} |".format(*row))

print("\nRoot of the equation: {:.3f}".format(root))
```
Output:
```
| Iteration |   a   |   b   |   c   |  f(a)  |  f(b) |  f(c)  |
|-----------|-------|-------|-------|--------|-------|--------|
|     1     | 3.000 | 6.000 | 4.333 | -4.000 | 5.000 | -2.222 |
|     2     | 4.333 | 6.000 | 4.846 | -2.222 | 5.000 | -0.592 |
|     3     | 4.846 | 6.000 | 4.968 | -0.592 | 5.000 | -0.126 |
|     4     | 4.968 | 6.000 | 4.994 | -0.126 | 5.000 | -0.026 |
|     5     | 4.994 | 6.000 | 4.999 | -0.026 | 5.000 | -0.005 |
|     6     | 4.999 | 6.000 | 5.000 | -0.005 | 5.000 | -0.001 |
|     7     | 5.000 | 6.000 | 5.000 | -0.001 | 5.000 | -0.000 |

Root of the equation: 5.000

```
In this code, we use the False Position method to find the root of the equation and record each iteration in a table that includes Iteration, a, b, c, and f(c).
