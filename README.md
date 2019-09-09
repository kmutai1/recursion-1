# recursion-1
"""
Lab 1: the power function
cs105 Introduction to Computer Science
Haverford College
<Kennedy Mutai>
Compute base to the exp power, for integer exp>=0,
using a straightforward translation of the rules
     base**0 = 1
     base**exp = base * base**(exp-1)
There are much more efficient algorithms for exponentiation,
but our emphasis here is on simplicity rather than speed.
Note that we do not allow negative or zero exponents,
  as our current algorithm does not handle them
Examples of the power function:
>>> power_using_recursion(5, 0)
1

>>> power_using_recursion(3, 3)
27

>>> power_using_recursion(3.0, 3)  # note that the ".0" is retained in the answer
27.0

>>> power_using_recursion(1.5, 2)   # 3/2 squared is 9/4
2.25

When we don't want to write out _all_ the digits of the answer,
we put the "# doctest: +ELLIPSIS" at the end of the example question, like so
>>> power_using_recursion(0.9, 5)  # doctest: +ELLIPSIS
0.5904900...

Testing for exceptions, read the following for further explanation on how to doctest exception
# https://docs.python.org/2.4/lib/doctest-exceptions.html
>>> power_using_recursion("2", 5)
Traceback (most recent call last):
TypeError: Base should be either integer or float

>>> power_using_recursion(2, 0.5)
Traceback (most recent call last):
TypeError: Exponent is supposed to be integer

>>> power_using_recursion(2, -5)
Traceback (most recent call last):
ValueError: Exponent should be positive integer or zero

Ignore warnings if you see any
"""

def power_using_recursion(base, exp):
    """postcondition: the result is the base raised to the exp power,
                      or a close approximation for information that
                      isn't represented exactly (such as real numbers)."""
    if not (isinstance(base, int) or isinstance(base, float)):
        raise TypeError("Base should be either integer or float")

    if not isinstance(exp, int):
        raise TypeError("Exponent is supposed to be integer")

    if isinstance(exp, int) and not exp>=0:
        raise ValueError("Exponent should be positive integer or zero")

    if exp == 1:
        return base
  
    else:
        assert(exp >= 0)
        return (base * power_using_recursion(base, exp-1))


def simple_power_ui():
    # doctest use, as per http://docs.python.org/lib/module-doctest.html
    import doctest
    print("Trying out tests given at the beginning of this script")
    doctest.testmod()

# The execution starts here
# I copied this from http://docs.python.org/lib/module-doctest.html
if __name__ == "__main__":
    simple_power_ui()
