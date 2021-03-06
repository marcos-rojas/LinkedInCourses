## Function definition
We can define some custom function with a description that can return a value. And we can also add
some parameters that are optional like *who="Collin"*
 ```python
 def least_difference(a, b, c, who="Colin"): #Collin is default value
    """Return the smallest difference between any two numbers
    among a, b and c.
    """
    diff1 = abs(a - b)
    diff2 = abs(b - c)
    diff3 = abs(a - c)
    return min(diff1, diff2, diff3)
  ```
Some functions can use functions as parameters like next example: (*higher order functions*)
 ```python
def mult_by_five(x):
    return 5 * x

def call(fn, arg):
    """Call fn on arg"""
    return fn(arg)

print(call(mult_by_five, 1),)
 ```
This are very useful and are integrated in some functions like in max function where choose criteria (module):

```python
 def mod_5(x):
    """Return the remainder of x after dividing by 5"""
 return x % 5
print('Which number is the biggest modulo 5?', max(100, 51, 14, key=mod_5), sep='\n',)
```
## Booleans and Conditionals
```python
 >>> 3.0 == 3
 True
 >>> '3' == 3
 False
```
We can also use conditionals (if, elif, else), operators (==, >=, <=, so on) and combination operations (and, or, not)
```python
def inspect(x):
    if x == 0:
        print(x, "is zero")
    elif x > 0:
    else:
        print(x, "is unlike anything I've ever seen...")
```python
When talk about *casting:* int are converted to True (except for 0), string are all True (except for ""), empty sequences always are False
