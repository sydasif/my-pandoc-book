# Understanding Mutable and Immutable Objects in Python

Python, is a popular and versatile programming language, the distinction between mutable and immutable objects is key concept to comprehend for effective Python programming. This concept significantly impacts how Python behaves in various situations. In this blog, we'll explore these concepts step by step, using code examples to make it clear.

## What Are Mutable and Immutable Objects?

In Python, we classify objects into two categories: mutable and immutable. Mutable objects can change their values after creation, while immutable objects stay the same once created.

### How Assignments Work

Let's start by understanding how assignments function in Python. When you assign a value to a variable, like `rtr_addr = "10.1.1.1"`, Python allocates memory to store that value, and the variable `rtr_addr` becomes a reference to that memory location.

```python
rtr_addr = "10.1.1.1"
```

It's essential to grasp that the variable's name and the actual object in memory are separate. If we add another variable, such as `gate_way = rtr_addr`, both names point to the same object in memory.

```python
gate_way = rtr_addr
```

Now, both `rtr_addr` and `gate_way` refer to the same string object in memory.

### Identifying Objects with `id()`

Python uses the `id()` function to identify the unique identity of an object. It helps us compare whether two names refer to the same object.

```python
id(rtr_addr)  # Output: 1513552872240
id(gate_way)  # Output: 1513552872240
```

The `id()` function returns a distinct identifier for each object in memory. When comparing the identities of `rtr_addr` and `gate_way`, we can determine if they refer to the same object.

## Immutable Objects in Python

In Python, we also have immutable objects, which cannot change their values once created. Even operations that seem to change their value actually create a new object with the updated value.

### Identifying Immutability

Let's consider an example to understand this better. Suppose we create a variable, `ssh_timeout`, and assign it the value `20`. We can use the `id()` function to check its identity.

```python
ssh_timeout = 20
id(ssh_timeout)  # Output: 1513546842960
```

The `id()` function returns a unique identifier for the object in memory. In this case, it's associated with the value `20`.

### Reassigning an Immutable Object

Now, if we reassign the `ssh_timeout` variable to a new value, like `ssh_timeout = 10`, a new object with the value `10` is created in memory. The variable `ssh_timeout` is updated to point to this new object, rather than modifying the original object.

```python
ssh_timeout = 10
id(ssh_timeout)  # Output: 1513546842640
```

The `id()` function returns a different identifier associated with the new value `10`.

### Incrementing/Decrementing Immutable Objects

Even when performing operations like incrementing or decrementing an immutable object, e.g., `ssh_timeout += 1`, a new assignment is happening. This results in creating a new object with the updated value, and the variable is updated to point to this new object.

```python
ssh_timeout += 1
id(ssh_timeout)  # Output: 1513546842672
```

Again, the `id()` function returns a different identifier after the assignment, representing the new object with the updated value.

### Types of Immutable Objects

In Python, several data types are considered immutable, including:

- `None`
- Booleans (`True` and `False`)
- Strings
- Integers
- Floats

These data types cannot be altered once created. Any operation that seems to modify them actually creates new objects, and the variables involved are updated to reference these new objects.

Understanding the concept of immutable objects in Python is crucial for designing and debugging your code. It ensures that you work within Python's fundamental rules and avoid unexpected behavior, especially when handling variables and data that should remain unaltered.

## Mutable Objects in Python

Python also has mutable objects, which can change their values after creation. Let's explore this concept, with a focus on lists as an example of mutable objects, and understand how they work internally.

### What Are Mutable Objects?

Mutable objects in Python are those that allow their values to be modified after they are created. Common examples of mutable objects include lists, dictionaries, and sets. In this section, we'll specifically look at lists to illustrate the concept.

### Working with Lists

Let's begin by creating a list called `data_center` containing several elements.

```python
data_center = ["sf", "la", "den", "dal"]
id(data_center)
```

The `id()` function checks the unique identifier associated with the `data_center` list, which points to a specific memory location.

### Modifying Lists

Now, let's expand the `data_center` list by adding a new element, "ny."

```python
data_center.append("ny")
id(data_center)
```

Surprisingly, even though we added an element to the list, the identifier for the list itself remains the same. This is because lists are mutable objects, and Python doesn't create a new list every time you modify it.

## The Internal Mechanism of Lists

To understand how lists work internally, it's crucial to know that Python allocates a continuous block of memory for the list when it's created. However, this memory doesn't store the actual elements but rather pointers to those elements.

### Memory Addresses

A list in Python functions as a container for references to objects, rather than a container for the objects themselves. When you create a list and populate it with elements, what the list stores are memory addresses (pointers) to the actual data objects.

For instance, consider this representation of memory for the `data_center` list:

| P1 | P2 | P3 | P4 | P5 |
|----|----|----|----|----|
| sf | la | den| dal| ny |

In this representation, P1, P2, P3, P4, and P5 are pointers to the actual elements of the list. The list doesn't directly contain the elements; it contains references to the memory addresses where these elements are stored in the computer's memory.

To gain a deeper understanding of this concept, you can check the `id()` of individual list elements:

```python
id(data_center[0])  # 1668505141296
id(data_center)     # 1668504824832
```

### Variable Assignment and List Mutability

When you create a new variable, such as `my_dc`, and assign it the value of the `data_center` list, both variables point to the same list in memory:

```python
my_dc = data_center
id(my_dc)  # 1668504824832
```

This means that modifying `my_dc` also affects the `data_center` list because they refer to the same object in memory. To avoid this behavior and work with an independent copy of the list, you can use the `copy()` method to create a shallow copy:

```python
my_dc = data_center.copy()
id(my_dc)  # 1668505142144
```

With a shallow copy, modifying one list doesn't affect the other, as they reference different memory locations.

In conclusion, understanding mutable objects in Python, such as lists, is crucial for effectively working with data structures and ensuring that changes made to variables are as expected. It's also essential to be aware of the internal mechanisms behind mutable objects to design robust and efficient code.
