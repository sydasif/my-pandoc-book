# Functions and Classes

In Python, the concept of functions plays a crucial role, allowing developers to encapsulate and reuse code efficiently. Functions provide a way to create modular and maintainable code, as specific tasks can be performed by calling a function multiple times, eliminating the need for redundant code.

Python's strength in object-oriented programming (OOP) further enhances its capabilities. In Python, almost everything is treated as an object, each associated with functions (methods), properties (attributes), and variables. A class serves as a blueprint in OOP, defining the structure and behavior of objects. Instances of a class can be created, essentially representing concrete examples based on the class's specifications.

When naming functions, objects, and modules in Python, adhere to the convention of using lowercase letters separated by underscores. For instance:

```python
def my_router():
    pass
```

On the other hand, when naming classes, follow the convention of capitalizing the first letter of each word without using underscores. For example:

```python
class UserProfile:
    pass
```

This naming convention enhances code readability and aligns with Python's style guidelines.

Python's functions are blocks of organized code designed to be reusable for specific tasks. They allow the efficient reuse of code segments and the creation of customized functions is straightforward. The syntax for defining a function in Python involves using the `def` keyword.

```python
def configure_router(router_name):
    print(f"{router_name} Configuration is completed.")

configure_router("R1")  # Calling the Function
```

Functions commence with the `def` keyword, followed by the function name and parentheses, which may include input parameters. The code block for each function is indicated by a colon. To invoke a function, simply use its name followed by parentheses. This structure promotes code clarity and the modular design of programs.

There are two types of functions in Python:

- Built-in Functions
- User-defined Functions

## Built-in Functions

Built-in functions are pre-written functions provided by the Python language and stored in its libraries. These functions are readily available for use and help streamline common tasks without the need to write code from scratch. Python boasts a range of built-in functions, including widely-used ones like dir() and sum().

## User-defined Functions

Python allows the creation of user-defined functions, which are functions declared by the programmer within their code. These functions are tailored to specific needs and tasks, providing a way to organize and reuse code for custom functionalities.

This distinction between built-in and user-defined functions showcases the versatility of Python, enabling developers to leverage both pre-existing functionalities and create their own tailored solutions.

## Return Values

In Python, if you do not explicitly specify a return value for a function, it automatically returns `None`. Let's explore this concept by calling a function and assigning its result to a variable.

```python
def configure_device(device_name):
    print(f"Configuring {device_name}")
    # Note: No explicit return statement, so it defaults to None

result = configure_device("Router1")
print(result)  # Output: None
```

In the example above, the `configure_device` function configures a network device and does not have a specific return statement, thus defaulting to `None`.

To make a function return a value, the `return` statement is used:

```python
def get_device_status(device_name):
    # Simulating some network automation logic
    status = "Online"
    return f"{device_name} is {status}"

device_status = get_device_status("Switch2")
print(device_status)  # Output: Switch2 is Online
```

In this network automation-related example, the `get_device_status` function simulates network logic and returns the status of a device. The returned value can be assigned to a variable for further use.

Furthermore, if a function does not encounter a `return` statement, or if it encounters a `return` statement without an expression, it automatically returns `None`. This behavior is designed to handle cases where a function is primarily intended for its side effects, such as printing information or modifying external variables, rather than producing a specific result.

Here's an example to illustrate this:

```python
def print_message(message):
    print(message)

result = print_message("Hello, World!")
print(result)  # Output: None
```

In this example, the `print_message` function prints a message but does not have a `return` statement. When the function is called and assigned to the variable `result`, `result` holds the value `None` because the function does not explicitly return anything.

It's worth noting that in Python, a function doesn't always have to return a value. Some functions are designed for their side effects, and the absence of a `return` statement implies a default return of `None`. If you need a function to explicitly return a value, you use the `return` keyword followed by the expression to be returned.

```python
def add_numbers(a, b):
    return a + b

result = add_numbers(3, 5)
print(result)  # Output: 8
```

In the `add_numbers` function, the `return a + b` statement explicitly returns the sum of `a` and `b`. If there were no `return` statement in this function, it would also return `None` by default.

## Function Arguments

In most functions, you can pass arguments to them. This is because you typically want to provide one or more values to a function, allowing it to perform actions based on these inputs.

In Python, the terms "parameter" and "argument" are often used interchangeably. However, there is a distinction between these two terms. Parameters are the variables defined when creating a function, while arguments are the actual values assigned to these parameters when the function is called.

## Positional Arguments

Positional arguments involve passing values to a function based on the order in which parameters are listed during the function definition. The order of these values is crucial, as they are assigned to corresponding parameters based on their position.

Consider the following example, where a function takes a single positional argument, `device_name`. When the function is called, a device name is provided, and it is used inside the function to print relevant information.

```python
def configure_device(device_name):
    print(f"Configuring {device_name}")

configure_device("Router1")
# Output: Configuring Router1
```

Here, the function `configure_device` expects a device name as a positional argument, and when calling the function with `"Router1"`, the device name is utilized inside the function for configuration.

When working with functions, arguments are specified after the function name, inside the parentheses. You can include as many positional arguments as needed, separating them with commas for clear organization and functionality.

## Default Arguments

Default arguments provide a way to make your functions callable with fewer arguments, offering flexibility in function calls. Unlike required arguments, which must be passed for the function to execute a task, default arguments come with predefined values.

Consider the following example, where a function `configure_device` has a regular argument, `device_name`, and a default argument, `configuration_mode`, which defaults to "basic."

```python
def configure_device(device_name, configuration_mode="basic"):
    print(f"Configuring {device_name} in {configuration_mode} mode.")

configure_device("Router1")
# Output: Configuring Router1 in basic mode.
```

In this example, the `configure_device` function takes a regular argument `device_name` and a default argument `configuration_mode`, which defaults to "basic." When calling the function without specifying `configuration_mode`, it defaults to the predefined value.

You can also explicitly specify values for both regular and default arguments:

```python
configure_device("Router2", configuration_mode="advanced")
# Output: Configuring Router2 in advanced mode.
```

Here, we specified both `device_name` and `configuration_mode` parameters, allowing flexibility in function calls. When dealing with default arguments, you can choose to specify positional arguments first, followed by keyword arguments. If values are passed without specifying their position, they will be assigned based on the order of parameters.

## Keyword (Named) Arguments

Sending arguments with the key=value syntax, known as keyword (named) arguments, provides a flexible way to call networking functions where the order of arguments becomes independent.

Consider the following example with a function `configure_network_device`:

```python
def configure_network_device(device_name, configuration_mode="basic", interface="eth0"):
    print(f"Configuring {device_name} in {configuration_mode} mode on interface {interface}.")

configure_network_device("Router1", configuration_mode="advanced", interface="eth1")
# Output: Configuring Router1 in advanced mode on interface eth1.
```

In this scenario, the function `configure_network_device` has a regular argument `device_name` and two default arguments, `configuration_mode` and `interface`. By using keyword arguments, the order of the arguments becomes flexible. This allows you to specify values for particular parameters, making your function calls more explicit.

With keyword arguments, the positions of the arguments become less critical. However, it's important to note that keyword arguments should come after positional arguments and before default arguments in a function call. Here's an example:

```python
configure_network_device("Router2", interface="eth2")
# Output: Configuring Router2 in basic mode on interface eth2.
```

In this case, we specified the `device_name` positionally and provided a value for the `interface` parameter using a keyword argument.

## `*args` and `**kwargs` in Functions

In functions, flexibility is key, and Python supports the concept of handling an arbitrary number of arguments and keyword arguments through `*args` and `**kwargs`.

**`*args` - An Arbitrary Number of Arguments**

```python
def network_status(*devices):
    print("Devices in the network:", devices)

network_status("Router1", "Switch2", "Firewall3")
# Output: Devices in the network: ('Router1', 'Switch2', 'Firewall3')
```

With `*args`, the function `network_status` can accept an arbitrary number of devices, making it suitable for scenarios where the number of devices in the network is not fixed.

**`**kwargs` - An Arbitrary Number of Keyword Arguments**

```python
def configure_device(**config_params):
    print("Configuration parameters:", config_params)

configure_device(device_type="Router", interface="eth0", vlan=10)
# Output: Configuration parameters: {'device_type': 'Router', 'interface': 'eth0', 'vlan': 10}
```

Using `**kwargs`, the function `configure_device` can handle an arbitrary number of keyword arguments, allowing for a more dynamic configuration approach.

## Handling Tuple and Dictionary as Arguments

```python
# Handling Tuple as Argument
my_tuple = (1, 2, 3)

def tup_output(*args):
    print("Tuple output:", args)

tup_output(*my_tuple)
# Output: Tuple output: (1, 2, 3)

# Handling Dictionary as Keyword Argument
my_dict = {'one': 1, 'two': 2}

def dict_output(**kwargs):
    print("Dictionary output:", kwargs)

dict_output(**my_dict)
# Output: Dictionary output: {'one': 1, 'two': 2}
```

Here, `*my_tuple` allows the function to extract individual values from the tuple, and `**my_dict` passes each key-value pair as keyword arguments.

Understanding `*args` and `**kwargs` provides a powerful mechanism for creating adaptable and versatile networking functions in Python.

## Scope of Variables in function

In Python, the scope of variables is crucial to understand, as variables can be either local or global. Local variables are declared within functions and are accessible only within those functions, while global variables are declared outside of functions and are accessible throughout the entire script, including within functions.

### Global Variables

Global variables are declared outside of any function in a Python script. They are accessible from anywhere in the code, including functions within the program.

```python
s = '5'

def num(n):
    print("local:", n)
    print("global:", s)

num(6)
# Output:
# local: 6
# global: 5
```

In this example, the variable `s` is declared globally and is accessible both within the function `num` and outside of it.

### Local Variables

Local variables are declared inside functions and are only accessible within the functions where they are defined. They cannot be accessed outside of the function.

```python
a = 5

def num():
    b = 3
    print(b)

num()
# Output: 3

print(a)
# Output: 5
```

Here, the variable `a` is global and can be accessed both inside and outside the function `num`. However, the variable `b` is local to the function `num` and cannot be accessed outside of it.

```python
# Attempting to access local variable b outside of the function
print(b)
# Output: NameError: name 'b' is not defined
```

If we attempt to access the local variable `b` outside of the function, it results in a `NameError` since `b` is not defined in the global scope.

Understanding variable scope is crucial for writing modular and maintainable networking scripts in Python.

As a network engineer diving into Python, these fundamental concepts pave the way for effective network automation. Functions, return values, arguments, and variable scope are the building blocks of modular, scalable, and maintainable networking scripts. By embracing Python's versatility, network engineers can streamline tasks, enhance efficiency, and adapt to the dynamic nature of networking environments.
