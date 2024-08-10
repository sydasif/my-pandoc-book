# Computer Programming - An Introduction

Inside every computer, there’s a special set of instructions that makes a computer to work, is called a computer program. It’s the essential life force that transforms computer hardware into a functional device. To help you understand this concept, think of a computer as a piano, an instrument that remains silent without a skilled musician.

However, computers, by their nature, are exceptionally proficient at executing some basic operations, such as addition and division, etc. A computer is performing these operations at lightning speed and with flawless accuracy.

Now, taking into a practical scenario. Imagine you’re on a long road trip, and you want to calculate your average speed. The distance you’ve traveled and the time it took to reach your destination, but here’s the problem, that  computers don’t intuitively understand these concepts as a human you do. Therefore, you need to provide precise instructions to the computer, as instructing it to:

- Accept a numerical value representing the distance.
- Accept a numerical value representing the travel time.
- Divide the distance by the time and store the result in memory.
- Display the result (average speed) in a human-readable format.

When combined, all these four apparently simple actions make a computer program. Even though these actions are different from that of what a computer naturally understands, they can be translated into a language that the computer can understand.

## Natural Languages vs. Programming Languages

Human language serve as tools for expressing intentions and transferring knowledge. Even though some languages require no spoken or written words, as they rely on gestures or body language, while others, like our mother tongue, enable us to convey our thoughts and reflect reality. Computers have their own language, known as machine language, which is complex and challenging for humans to understand fully.

It’s important to note that even the most advanced computers lack true intelligence, because they responded solely to a predefined set of known commands, often very basic ones. Think of it as computers following orders like “take this number, divide it by another, and save the result.” This set of known commands is referred to as an instruction list or `IL`.

> *Note*: machine languages are also created by humans.

### The anatomy of a language

Every language, whether natural or machine-based, comprises the following key elements:

- ***Alphabet:*** A set of symbols used to construct words within the language.
- ***Lexis (Dictionary):*** A collection of words and their meanings within the language.
- ***Syntax:*** A set of rules governing the structure of sentences and phrases.
- ***Semantics:*** A set of rules determining the meaning of a given phrase or sentence.

In the case of machine language, the `IL` serves as the alphabet (`zeroes` and `ones`). However, humans require a more expressive language to write programs—one that computers can execute. These languages, often known as high-level programming languages, share similarities with natural languages. They have symbols, words, and conventions that humans can understand, high-level languages empower humans to issue commands to computers.

A program written in a high-level programming language is referred to as `source code`, and the file containing this source code is known as a `source file`.

### Compilation vs. interpretation

Computer programming involves composing elements of a selected programming language in a manner that achieves the desired outcome. This outcome has depending on the programmer’s imagination, knowledge, and experience.

There are two primary methods for translating a program from a high-level programming language into machine language:

1. ***Compilation:*** The source program is translated once to create a file containing machine code. This resulting file can be distributed globally, and the program responsible for this translation is known as a `compiler`.

2. ***Interpretation:*** The source program is translated each time it needs to run. The program performing this kind of transformation is an `interpreter`, as it interprets the code every time it’s executed. This also implies that you can’t distribute the source code as-is; the end-user also requires the interpreter to execute it.

#### Compilation — advantages and disadvantages

- **Advantages**:
  - Executed code is typically faster.
  - Only the user needs the compiler; the end-user can use the code without it.
  - The translated code is stored in machine language, keeping it secure.

- **Disadvantages**:
  - Compilation is a time-consuming process; you can’t run your code immediately after making changes.
  - You require a compiler for each hardware platform you want your code to run on.

#### Interpretation — advantages and disadvantages

- **Advantages**:
  - You can run the code as soon as you finish writing it; no need for additional translation phases.
  - The code is stored in a programming language, not machine language. It can run on computers with different architectures without separate compilation.

- **Disadvantages**:
  - Interpretation doesn’t result in high-speed execution; your code shares resources with the interpreter.
  - Both you and the end-user require the interpreter to run your code.

Python falls into the category of interpreted languages. To program in Python, you’ll need a Python interpreter. Without it, you won’t be able to execute your code. The best part is that Python is free, making it one of its most significant advantages. Languages designed for interpretation are often referred to as scripting languages, and the source programs written in them are called scripts.

## Understanding Python Language

Python is a widely-used, interpreted, object-oriented, high-level programming language with dynamic semantics. It’s employed for general-purpose programming and is known for its versatility. The name “Python” comes from an old BBC television comedy sketch series called Monty Python’s Flying Circus.

Python’s creation is credited to *Guido van Rossum*, born in `1956` in Haarlem, the Netherlands. While Python’s popularity has grown worldwide, it’s essential to acknowledge that it all started with Guido’s vision.

In `1999`, *Guido van Rossum* outlined his goals for Python:

- Create an easy, intuitive, and powerful language.
- Keep it open source.
- Make it understandable, like plain English.
- Ensure it’s suitable for everyday tasks, allowing for short development times.
- Python has matured and gained trust in the programming world. It’s not just a flash in the pan but a bright star in the programming firmament.

### What sets Python apart?

There are numerous reasons why Python stands out, as we’ve mentioned earlier. Let’s summarize them practically:

- Easy to Learn: Learning Python takes less time compared to many other languages, allowing you to start programming quickly.
- Easy to Teach: Teaching Python is more straightforward, focusing on programming techniques rather than complex language intricacies.
- Easy to Use: Python often lets you write code faster when creating new software.
- Easy to Understand: Python code is generally easier to comprehend, making it simpler to read and maintain.
- Easy to Obtain, Install, and Deploy: Python is free, open-source, and cross-platform, making it accessible to all.

It’s worth noting that Python is not the only solution in the programming landscape.

### Python’s competitors

Python has two direct competitors that share similar properties and capabilities:

- Perl: A scripting language.
- Ruby: Another scripting language.

Perl leans towards tradition and convention and has similarities with older languages derived from classic C programming. On the other hand, Ruby is more progressive and filled with fresh ideas. Python finds its place somewhere between these two options.

Python’s growth is evident as more development tools are implemented in Python. Many everyday use applications are being written in Python, and numerous scientists have abandoned expensive proprietary tools in favor of Python.
