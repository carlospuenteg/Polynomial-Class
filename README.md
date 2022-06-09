# Polynomial Class in Python

```python
class P:
    # Create the polynomial with the given coefficients
    def __init__(self, *coeffs):
        self.coeffs = coeffs

    # Get the value of the polynomial with a given x
    def p(self, x):
        return sum(coef*(x**(len(self.coeffs)-1-exp)) for exp,coef in enumerate(self.coeffs))

    # Show the polynomial
    def __str__(self):
        toret = ""
        max_exp = len(self.coeffs) - 1
        for exp,coef in enumerate(self.coeffs):
            exp = max_exp - exp
            if coef != 0:
                var = "x" if exp != 0 else ""
                sp = " " if exp != max_exp else ""
                coef = f"{sp}{'-' if coef < 0 else '+' if exp != max_exp else ''}{sp}{abs(coef) if abs(coef) != 1 or exp == 0 else ''}"
                exp = f"^{exp}" if exp > 1 else ""
                toret += f"{coef}{var}{exp}"
        return toret
```

## Examples

```python
p = P(1, -2, 3)
print(p)            #>> x^2 - 2x + 3
print(p.p(0))       #>> 3
```
```python
p = P(-1, 0, -2)
print(p)            #>> -x^2 - 2
print(p.p(-2))      #>> -6
```
```python
p = P(-2, 5, 12, 3, 0)
print(p)            #>> -2x^4 + 5x^3 + 12x^2 + 3x
print(p.p(3))       #>> 90
```
```python
p = P(0.03, -0.5)
print(p)            #>> 0.03x - 0.5
print(p.p(3))       #>> -0.41000000000000003
```