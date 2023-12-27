# Understanding Python Numbers

Numbers in Python are a fundamental data type used for various mathematical operations and calculations. There are primarily two numeric data types in Python: integers (int) and floating-point numbers (float).

1. *Integers Numbers (int):* Integers are typically used when working with discrete values or countable objects. They can be positive, negative, or zero. For example, 5, -10, and 0 are all integers in Python. Integers are typically used when you need to work with discrete values or countable objects.

2. *Floating-Point Numbers (float):* Floating-point numbers, or floats, are numbers that include a decimal point or use scientific notation, such as 3.14 or 2.5e-3. Floats are used when you need to work with real numbers, including fractional values and approximate calculations.

These two numeric data types are essential for handling a wide range of mathematical and numerical operations in Python, making it a versatile language for tasks involving arithmetic and mathematical computations.

## Integers in Python

Python provides a versatile set of tools for working with integers, a fundamental data type, including creating, type checking, and standard mathematical operations. Here's how you can use these features:

### Creating an integer

To create an integer variable, simply assign a whole number to it. For instance:

```python
Python 3.10.7 ............. [MSC v.1933 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> my_var = 22
>>> print(my_var)
22
```

In this example, we assigned the integer value 22 to the variable `my_var`.

### Type checking of integer

You can check the data type of a variable using the `type()` function. For instance:

```python
Python 3.10.7 ............. [MSC v.1933 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> my_var = 22
>>> print(type(my_var))
<class 'int'>
```

This indicates that `my_var` is of integer type.

## Math Operations with Integers

Python allows you to perform standard mathematical operations on integers:

- *Addition:* You can add two integers using the `+` operator:

```python
Python 3.10.7 ............. [MSC v.1933 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> result = 17 + 22
>>> print(result)
39
```

The result variable now holds the value `39`.

- *Subtraction:* Subtraction is done using the `-` operator:

```python
Python 3.10.7 ............. [MSC v.1933 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> result = 22 - 7
>>> print(result)
15
```

The `result` variable now contains the value `15`.

- *Multiplication:* Multiplication is performed with the `*` operator:

```python
Python 3.10.7 ............. [MSC v.1933 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> result = 3 * 4
>>> print(result)
12
```

The `result` variable now contains the value `12`.

- *Division:* Division is carried out with the `/` operator. For instance:

```python
Python 3.10.7 ............. [MSC v.1933 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> result = 4 / 7
>>> print(result)
0.5714285714285714
```

The `result` variable now contains the float value `0.5714285714285714`.

These basic operations are essential for manipulating integer values, making Python a powerful language for various mathematical computations and data manipulation tasks.

## Floats in Python

In Python, working with floating-point numbers (floats) is just as straightforward as working with integers. Here's how you can create, check the data type, and perform standard mathematical operations with floats:

### Creating a float

To create a float variable, assign a number with a decimal point to it. For example:

```python
Python 3.10.7 ............. [MSC v.1933 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> my_var = 3.3
>>> print(my_var)
3.3
```

In this case, we've assigned the float value `3.3` to the variable `my_var`.

### Type checking of float

You can verify the data type of a variable using the `type()` function. For example:

```python
Python 3.10.7 ............. [MSC v.1933 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> my_var = 3.3
>>> print(type(my_var))
<class 'float'>
```

When you run this code, it will produce the output; `<class 'float'>` this confirms that `my_var` is a float.

## Math Operations with Floats

Python allows you to perform standard mathematical operations on float values:

- *Addition:* You can add two float numbers using the `+` operator:

```python
Python 3.10.7 ............. [MSC v.1933 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> result = 3.3 + 2.2
>>> print(result)
5.5
```

he result variable now holds the value `5.5`, the sum of the two floats.

- *Division:* Division is performed with the `/` operator:

```python
Python 3.10.7 ............. [MSC v.1933 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> result = 7 / 2
>>> print(result)
3.5
```

The `result` variable now contains the float value `3.5`, which is the result of dividing `7` by `2`.

- *Multiplication:* Multiplication is carried out with the `*` operator:

```python
Python 3.10.7 ............. [MSC v.1933 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> result = 3.1 * 2.5
>>> print(result)
7.75
```

The `result` variable now contains the value `7.75`, which is the product of `3.1` and `2.5`.

### Rounding numbers

You can round float numbers using the `round()` function. For instance, to round the result of `4` divided by `3` to the nearest integer:

```python
Python 3.10.7 ............. [MSC v.1933 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> result = round(4 / 3)
>>> print(result)
1
```

The result variable now holds the integer value `1`, which is the result of rounding `4/3`.

Floats are essential for handling real numbers and approximate calculations, making Python a versatile language for various mathematical computations and scientific applications.

## Numbers - Other Operators

In addition to basic arithmetic operations, Python provides other operators for working with numbers. Here are two commonly used number operators:

### Modulo operator (%)

The modulo operator, represented by `%`, calculates the remainder when one number is divided by another. For example:

```python
Python 3.10.7 ............. [MSC v.1933 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> result = 9 % 2
>>> print(result)
1
```

The result variable will hold the value `1` because `9` divided by `2` leaves a remainder of `1`.

### Power operator (**)

The power operator, represented by `**`, raises a number to a specified exponent. For instance:

```python
Python 3.10.7 ............. [MSC v.1933 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> result = 2 ** 3
>>> print(result)
8
```

The result variable will hold the value `8` because `2` raised to the power of `3` is `8`.

These operators expand the range of mathematical operations you can perform in Python, allowing for tasks like finding remainders and calculating exponents in your numerical computations.

## Incrementing Counters

When working with counters in Python, you can increment or decrement their values in various ways. Here are some common methods to do so:

### Using assignment operator

You can initialize a counter with an initial value, and then increment it using the assignment operator. For example:

```python
Python 3.10.7 ............. [MSC v.1933 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> i = 0   # Initialize i to 0
>>> i = i + 1   # Increment i by 1
>>> print(i)
1
```

After these operations, the variable `i` hold the value `1`.

### Using augmented assignment

A more concise and common way to increment a counter is to use the augmented assignment operator (`+=`). For example:

```python
Python 3.10.7 ............. [MSC v.1933 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> i = 0   # Initialize i to 0
>>> i += 1  # Increment i by 1
>>> print(i)
1
```

This code achieves the same result as the previous example, with the variable `i` also holding the value `1`.

## Decrementing a Counter

The process of decrementing a counter is similar to incrementing, but you subtract a value instead. For example:

```python
Python 3.10.7 ............. [MSC v.1933 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> i = 10   # Initialize i to 10
>>> i = i - 1   # Decrement i by 1
>>> print(i)
9
```

After these operations, the variable `i` hold the value `9`. You can achieve the same result using the augmented assignment operator for decrement:

```python
Python 3.10.7 ............. [MSC v.1933 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> i = 10   # Initialize i to 10
>>> i -= 1   # Decrement i by 1
>>> print(i)
9
```

In this case, the variable `i` also ends up with the value `9`.

These techniques are commonly used for maintaining and updating counters in loops, tracking progress, and controlling the flow of your code when you need to count or iterate through a series of values.
