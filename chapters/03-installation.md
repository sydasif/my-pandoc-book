# Python for Network Engineers

Python, a versatile and powerful programming language, has become a must-have tool for network engineers. Whether you're just starting in networking or an experienced pro, Python offers a wealth of benefits for network-related tasks. Let's explore these key aspects and guide you through the basics of Python for network engineering.

**Network Automation:** It helps network engineers automate repetitive tasks such as making configuration changes, creating backups, and monitoring networks.

**Configuration Management:** Python-based tools, including Ansible, NAPALM, and Netmiko, are widely used for configuration management.

**Monitoring and Troubleshooting:** Python allows network engineers to create custom monitoring and troubleshooting tools that continuously check the health of a network.

**Network Security:** Python plays a vital role in implementing strong security policies, analyzing network traffic, and responding to security incidents.

**Cross-Platform Compatibility:** Networking involves various operating systems and devices. Python's cross-platform compatibility means that code written in Python can run on different operating systems without significant changes.

In summary, Python empowers network engineers to streamline operations, improve network efficiency, and enhance security. Whether you're managing a small network or a large infrastructure, Python equips you to handle network automation tasks with greater efficiency and effectiveness.

## Python Installation

Before you begin using Python for network automation, it's important to understand how to set up Python on your specific operating system. Let's go through this initial step.

### On Windows

While Python may not be pre-installed on Windows, the installation process is simple:

1. Visit the official Python [website](https://www.python.org/downloads/windows/) and download the Windows installer for your desired Python version.
2. Run the installer and follow the installation wizard's instructions. Make sure to select the option to "Add Python to PATH" during installation.

### On MacOS

Python is often pre-installed on MacOS, but you may prefer to manage your Python installation:

1. Download the Python installer for MacOS from the official [website](https://www.python.org/downloads/mac-osx/).
2. Run the installer and follow the installation instructions. 
3. Although MacOS typically comes with Python 2.7, it's advisable to install the latest Python 3 version for compatibility with newer Python packages.

### On Linux

Linux distributions typically include Python, but specific packages may need to be installed:

- For Debian/Ubuntu-based systems, you can use `apt` to install Python:

```bash
$ sudo apt update
$ sudo apt install python3
```

- For Red Hat/Fedora-based systems, you can use `dnf` or `yum`:

```bash
$ sudo dnf install python3
$ sudo yum install python3
```

For other Linux distributions, consult your system's package manager for the appropriate commands.

### Python interpreter

The Python interpreter is your way to run Python scripts and execute code. This interactive environment allows you to experiment with Python code, making it an important tool for learning and developing in Python. Here's how to use the Python interpreter:

1. Open your terminal or command prompt.
2. Type `python` or `python3` and press Enter. You should see the Python interpreter prompt (`>>>`), indicating that you're in interactive mode.

Now, you can enter Python code directly, and the interpreter will execute it. For example, try entering `print("Hello, Python!")`, and you'll see the output immediately.


```python
Python 3.10.7 ............. [MSC v.1933 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> print("Hello, Python!")
Hello, Python!
```

The Python interpreter is an excellent way to test small pieces of code, experiment with Python features, and quickly see the results. Let’s start by simply creating a variable called `hostname` and assigning it a value:

```python
Python 3.10.7 ............. [MSC v.1933 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> hostname = 'router'
```

As you see, there is no need to declare the variable first or define that `hostname` is going to be a `string`. This is the reason Python is called a dynamic language, differing from some programming languages such as C and Java. Now, you can print the variable:

```python
Python 3.10.7 ............. [MSC v.1933 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> hostname = 'router'
>>> print(hostname)
router
>>> hostname
'router'
```

Once a variable is assigned, we can easily print it using the `print()` command. However, while in the Python shell, you can also print `hostname` value or any other variable by just typing in the name of the variable and pressing `Enter` key. It's particularly helpful when you're learning Python or troubleshooting issues in your scripts.

## Assignment Operator and Variable

Python uses a straightforward syntax for variable assignment. Here are some examples:

```python
Python 3.10.7 ............. [MSC v.1933 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> test = 'test'
>>> ip_addr = '192.168.1.1'
```

Variable assignment in Python is flexible and forgiving, offering room for creativity. However, it's essential to follow some best practices to write clean and maintainable code.

### Use descriptive names

Choose variable names that are descriptive and convey their purpose. Avoid generic names like `temp` or `data`. Instead, use names like `ip_address` or `server_name` to make your code more readable.

### Use underscores

For multi-word variable names, use underscores to separate words, following the snake_case convention. For example, `device_name` is more readable than `deviceName`.

### Avoid reserved words

Be careful not to use Python's reserved words as variable names. For example, naming a variable `print` or `for` can lead to unexpected behavior.

### Consistency

Maintain consistency in your variable naming. If you use `ip_address` in one part of your code, don't switch to `ip_addr` elsewhere. Consistency simplifies code comprehension.

## Python Naming Convention

Following naming conventions is essential for writing clean and maintainable Python code. Common conventions include:

- *snake_case_lower* for variables and functions.
- *PascalCase* for class names.
- *SNAKE_CASE_UPPER* for constants.

Let's dive deeper into naming conventions, focusing on the following aspects:

### Variable names

- Start variable names with a lowercase letter or underscore.
- Use clear and descriptive names that convey the variable's purpose.
- For multi-word variable names, use underscores for separation (e.g., `user_id`).

### Function names

- Begin function names with a lowercase letter or underscore.
- Use descriptive names that hint at the function's action or purpose.
- For multi-word function names, use underscores (e.g., `calculate_speed`).

### Class names

- Start class names with an uppercase letter.
- Use CamelCase, where each word in the name begins with an uppercase letter and has no underscores (e.g., `NetworkDevice`).

### Constant names

- Constant variables should be in uppercase with words separated by underscores (e.g., `MAX_CONNECTIONS`).

By following these nuanced naming conventions, you'll make your Python code more accessible and comprehensible to yourself and others who collaborate on your projects.

## Print Function

The `print()` function is a fundamental tool for displaying output in Python. It allows you to communicate information to users, debug your code, and provide feedback. To use the `print()` function, follow this format:

```python
Python 3.10.7 ............. [MSC v.1933 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> print("Hello, Python!")
Hello, Python!
```

Here, the text enclosed in double quotes is the message you want to display. You can print variables, numbers, or any other data type using the `print()` function.

## Input Function

The `input()` function is equally important. It enables your Python programs to interact with users by accepting input from them. The `input()` function presents a prompt to the user, and the user's input is returned as a string. Here's an example of using the `input()` function:

```python
Python 3.10.7 ............. [MSC v.1933 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> user_input = input("Please enter your name: ")
Please enter your name: John
>>> print("Hello, " + user_input + "!")
Hello, John!
```

In this example, the `input()` function displays the message "Please enter your name: " and waits for the user to type their name. The user's input is then stored in the `user_input` variable.

## Python Characteristics

Understanding key characteristics of Python can help you write cleaner code:

### Indentation

Indentation is a fundamental aspect of Python's syntax. Unlike many programming languages that use curly braces `{}` to define code blocks, Python relies on indentation. Proper indentation ensures that your code is structured correctly and is a crucial aspect of Python's readability.

### Use of spaces

Consistent use of spaces is essential in Python, particularly for indentation. The recommended standard, according to the PEP8 style guide, is to use four spaces for each level of indentation. Adhering to this standard enhances code readability and maintainability.

### Python script and executing

To create and execute a Python script, follow these steps:

- Create a Python script file with a `.py` extension, for instance, `my_code.py`.
- In Linux or MacOS, you can include a "shebang" line at the beginning of your script to specify the Python interpreter to use.

```bash
#!/usr/bin/env python
```

This line tells the system to use the Python interpreter located at `/usr/bin/env python`. It ensures that your script runs with the correct Python version.

- If needed, adjust the script's permissions to make it executable. You can use the `chmod` command on Unix-based systems:

```bash
$ chmod +x my_code.py
```

This command makes the script executable.

- On Windows, run the script using the following command:

```bash
$ python my_code.py
```

Alternatively, you can use the Python launcher with the `py` command:

```bash
$ py my_code.py
```

Here's an example script:

```python
#!/usr/bin/env python
ip_addr = input("Enter an IP Address: ")
print("You entered:", ip_addr)
```

By following these steps, you can create, execute, and manage Python scripts efficiently.

### Comments in code

Comments play a pivotal role in documenting your code and assisting both yourself and others in understanding the purpose of different parts of your script. Python supports single-line comments that begin with the `#` symbol. You can also include inline comments for additional context:

```python
Python 3.10.7 ............. [MSC v.1933 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> # This is a comment
>>> ip_addr = "10.1.1.1"
>>> # This line prints the IP address
>>> print(ip_addr)
10.1.1.1
```

For multi-line comments, Python allows the use of triple-quotes (`'''`) or (`"""`) at the beginning and end of the comment block.

## `dir` and `help` Function

Python equips you with useful tools, such as the `dir()` function and the `help()` function. These tools are invaluable for exploring and comprehending Python libraries and modules as you apply them to your network engineering tasks.

The `dir()` function lists the attributes and methods of objects, providing insights into the capabilities of an object or module. For example, if you want to explore the functionality of a Python module like `os`, you can use `dir(os)` to see a list of functions and attributes it offers.

```python
Python 3.10.7 ............. [MSC v.1933 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> import os
>>> dir(os)   
# Output is omitted
['readlink', 'remove', ..... 'walk', 'write']
```

The `help()` function, on the other hand, provides detailed information about specific functions or modules. You can use it to get documentation and usage examples for Python functions and libraries. For instance, you can type `help(os)` to access information about the `os` module.

To learn how to use a method that you see in the output of `dir()` function, we can use the built-in function `help()`. The example below shows how we can use `help()` function to use the upper method:

```python
Python 3.10.7 ............. [MSC v.1933 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> dir(hostname)
# Output is omitted
['partition', .... 'upper', 'zfill']
>>> help(hostname.upper)
Help on built-in function upper:

upper() method of builtins.str instance
    Return a copy of the string converted to uppercase.

```

Here is the recommended flow to use these Python tools:

1. Check your data type by using `type()`.
2. Check the available methods for your object by using `dir()`.
3. After knowing which method you want to use, learn how to use it by using `help()`.

These tools can be used on any Python object, not on strings only.

Python has become an indispensable tool for network engineers, offering automation capabilities for tasks like configuration management, monitoring, and security. It facilitates rapid prototyping, cross-platform compatibility, and data analysis, making it a versatile asset in managing networks of all sizes.
