# Conditional Statements in Python

In Python, conditional statements play a pivotal role in controlling the flow of your program. They allow you to execute specific blocks of code based on the truth value (True or False) of certain conditions.

An **expression** is a fundamental concept in Python, representing a piece of code that can be evaluated to produce a value. Expressions typically involve variables, constants, and operators. Conditions, which determine the execution of code blocks, are constructed using these expressions.

Let's delve into the key conditional statements in Python:

**if statement**: This fundamental construct enables you to execute a block of code when a given condition evaluates to True. It's a core element of Python's conditional logic.

**elif statement**: When you need to evaluate multiple conditions one after another, the `elif` statement comes into play. It allows you to check a series of conditions, and when one of them proves to be true, the corresponding code block is executed.

**else statement**: For scenarios where none of the preceding conditions are true, the `else` statement provides a default code block to execute. It acts as a safety net, ensuring that there's always some code to run when no other conditions match.

These conditional statements are powerful tools for making your Python programs responsive and adaptable, enabling them to cater to a variety of scenarios based on the truth or falsity of specific conditions.

## Importance of Conditions in Programming

Conditions are a fundamental building block of programming, making your code dynamic and responsive. They empower you to make decisions based on various factors and direct your program's execution along different code paths.

Consider the following Python code snippet:

```python
ip_addr = "10.1.1.1."
if "10" in ip_addr:
    print("Address Found")
```

In this example, we have a variable, `ip_addr`, which holds an IP address represented as a string. The `if` statement is employed to assess whether the string `10` exists within `ip_addr`. If this condition holds true, the indented block of code beneath the `if` statement is executed, resulting in the display of "Address Found." The critical element here is the condition, expressed as `"10" in ip_addr`. This condition evaluates to `True` when the string `10` is located within `ip_addr`, and to `False` otherwise.

## Conditional Statements - `elif` and `else`

The `elif` statement serves as a valuable tool for checking an additional condition when the preceding `if` condition evaluates to `False`. If the initial `if` condition proves to be `True`, the code within the corresponding `if` block is executed. However, if it turns out to be `False`, Python proceeds to evaluate the condition following the `elif` statement.

Let's illustrate this with a Python code snippet:

```python
ssh_timeout = 20
if ssh_timeout == 10:
    print("SSH TimeOut: 10 sec")
elif ssh_timeout > 30:
    print("SSH TimeOut Greater Than: 30 sec")
else:
    print("Unexpected SSH TimeOut")
```

In this example, if the variable `ssh_timeout` equals `10`, it will display "SSH TimeOut: 10 sec." Conversely, if `ssh_timeout` surpasses `30`, the program will output "SSH TimeOut Greater Than: 30 sec." And should both of these conditions prove `False`, it will fall back to the `else` block, printing "Unexpected SSH TimeOut."

The `else` statement serves as a safety net, ensuring that there's a predefined course of action when none of the prior conditions match the situation at hand. This combination of `if`, `elif`, and `else` allows your code to gracefully handle a variety of scenarios, making your programs more robust and adaptable.

## Comparison Operators and Conditionals

Comparison operators are essential in your decision-making process by allowing you to establish relationships between values. These operators are fundamental building blocks of conditional statements, enabling your code to adapt and respond to different circumstances based on the comparisons made.

- `==` (equal)
- `!=` (not equal)
- `<` (less than)
- `>` (greater than)
- `<=` (less than or equal to)
- `>=` (greater than or equal to)

Let's revisit the previous Python example:

```python
ssh_timeout = 20
if ssh_timeout == 10:
    print("SSH TimeOut: 10 sec")
elif ssh_timeout > 30:
    print("SSH TimeOut Greater Than: 30 sec")
else:
    print("Unexpected SSH TimeOut")
```

In this instance, the `==` and `>` comparison operators are employed to assess whether the value of `ssh_timeout` aligns with specific criteria.

Comparison operators provide a means to compare values in conditions.

## Logical Operators and Conditional Statements

Logical operators serve as valuable tools for merging multiple conditions into a single expression, facilitating intricate decision-making in your code.

Let's illustrate their utility with a Python example:

```python
ssh_timeout = 20
ip_addr = "10.1.1.1"
host_reachable = True

if host_reachable and ssh_timeout >= 10:
    print("Try to connect")
elif not host_reachable or ip_addr == "10.1.1.1":
    print("Invalid host, do not try connection")
else:
    print("Unexpected error, do something")
```

In this code, `and` and `or` are employed to combine conditions, allowing you to create more intricate decision structures.

For instance, the `if` statement checks if the host is reachable and the SSH timeout is greater than or equal to `10` before attempting a connection.

The `elif` statement uses `not` to negate the "host_reachable" condition or checks if `ip_addr` equals `10.1.1.1` to determine whether the host is invalid. When none of these conditions hold, the `else` block handles unexpected errors.

## Nested Conditional Statements

When you find yourself dealing with numerous conditions, you can employ nested conditionals, which involve placing conditionals within other conditionals.

Let's consider this Python example:

```python
ssh_timeout = 20
host_reachable = True

if host_reachable:
    if ssh_timeout is not None:
        print("Try to connect")
    else:
        print("Unexpected error, do something")
```

In this scenario, we have an outer conditional statement (`if host_reachable`) and an inner conditional statement (`if ssh_timeout is not None`). Depending on the combination of these conditions, distinct code blocks are executed.

Nested conditionals can extend to multiple levels of depth, providing you with the flexibility to craft intricate decision-making processes in your code. This hierarchy of conditionals ensures that your program can respond to a wide range of scenarios with precision and sophistication.

## Truthy and Falsy Values in Python

Every value in Python is assessed as either truthy or falsy. Truthy values are those that Python interprets as representing the truth. These values evaluate to `True` when used in conditional expressions. Common examples of truthy values include non-zero numbers, non-empty strings, and any objects or collections that are not empty.

Conversely, falsy values are those that Python interprets as representing falsehood. These values evaluate to `False` when used in conditional expressions. Common falsy values include:

- `0` (integer zero)
- `0.0` (float zero)
- `''` (empty string)
- `None` (a special Python value indicating the absence of a value)
- Empty collections like lists, dictionaries, and sets

Let's look at a practical example:

```python
ssh_timeout = 0

if not ssh_timeout:
    print("Error, no SSH timeout")
# Output: Error, no SSH timeout
```

In this code, the value of `ssh_timeout` is set to `0`, which is one of the falsy values. The condition `if not ssh_timeout` checks whether `ssh_timeout` is falsy, and if it is, the program proceeds to execute the code within the `if` block, resulting in the message "Error, no SSH timeout" being printed.

By leveraging the truthy and falsy nature of values, you can design conditional statements that make decisions based on whether data is meaningful or absent. This capability is crucial for creating robust and adaptive code that responds intelligently to a variety of data scenarios.

## Idiomatic Expressions in Python

In Python, idiomatic expressions are not just a matter of correct syntax; they also relate to writing code in a way that is clear, efficient, and easy to understand. The use of idiomatic expressions improves code readability.

```python
ssh_timeout = 20
ip_addr = None
host_reachable = False

if ssh_timeout is None:  # ssh_timeout == None in not idiomatic
    print("Error, no SSH timeout")
```

- **Idiomatic**: Using `is None` for checking if a variable is `None` is the preferred way. This approach is more explicit and makes the code's intent clear, instead of using `ssh_timeout == None` is not idiomatic. While it may work, it's not the recommended way to check for `None`.

```python
if host_reachable is False:  # host_reachable == False
    print("Error, host is not reachable")
```

Instead of explicitly checking if a boolean variable is `False`, you can use the variable itself in a boolean context, which is more readable. For example, `host_reachable == False` conveys the same meaning without explicitly comparing to `False`.

```python
if ip_addr is not None:  # ip_addr != None
    print("Error, no SSH timeout")
```

The code for checking if a variable is not `None` is idiomatic and follows the recommended practice, instead of `ip_addr != None`.

In addition to readability, adhering to idiomatic expressions can often improve code consistency and maintainability. Most Python linters, which are tools for static code analysis, are configured to catch non-idiomatic expressions and can help ensure your code follows best practices.
  
## Conclusion

Conditionals are a fundamental part of programming that allow you to make decisions, control the flow of your code, and handle different scenarios. With comparison, and logical operators, you can create dynamic and responsive code that meets various conditions and requirements. Whether you're dealing with simple choices or complex decision-making, conditionals are an essential tool in your programming arsenal.
