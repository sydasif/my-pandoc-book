# Python

* Lists are declared within `[]` and elements are separated by `,`
* Each element can be of any data type, including list data type

## Example

Use `for` loop to iterate over a list.

```python
numbers = [2, 12, 3, 25, 624, 21, 5, 9, 12]
odd_numbers = []
even_numbers = []

for num in numbers:
    odd_numbers.append(num) if(num % 2) else even_numbers.append(num)

print(f'numbers:      {numbers}')
print(f'odd_numbers:  {odd_numbers}')
print(f'even_numbers: {even_numbers}')
```

# Ruby

* Arrays are declared within `[]` and elements are separated by `,`
* Each element can be of any data type, including array data type

## Example

Use `each` method to iterate over an array.

```ruby
numbers = [2, 12, 3, 25, 624, 21, 5, 9, 12]
odd_numbers = []
even_numbers = []

numbers.each { 
    |n| n.even? ? even_numbers.append(n) : odd_numbers.append(n) 
    }

puts "numbers:      #{numbers}"
puts "odd_numbers:  #{odd_numbers}"
puts "even_numbers: #{even_numbers}"
```

# CLI

Executing the Python and Ruby programs mentioned in previous chapters:

```bash
$ python3.7 list_looping.py
numbers:      [2, 12, 3, 25, 624, 21, 5, 9, 12]
odd_numbers:  [3, 25, 21, 5, 9]
even_numbers: [2, 12, 624, 12]

$ ruby array_looping.rb
numbers:      [2, 12, 3, 25, 624, 21, 5, 9, 12]
odd_numbers:  [3, 25, 21, 5, 9]
even_numbers: [2, 12, 624, 12]
```

## Quote

> This is a quote

## Links

This is a sample [GitHub style markdown](https://github.github.com/gfm/) file.
Top level headers are chapters and other headings are for sub-sections.

# Back Ground

By default, `background` is set to `null`.

Can be changed to different color to suit the chosen theme.

```python
# sample comment: a/b != a\b

>>> 2 ** 5
32
```

Executing Python program from shell:

```bash
$ python3.7 list_looping.py
numbers:      [2, 12, 3, 25, 624, 21, 5, 9, 12]
odd_numbers:  [3, 25, 21, 5, 9]
even_numbers: [2, 12, 624, 12]
```

Just another line.

# Syntax 

* Using `python` syntax highlighting

```python
# remove first two columns where : is delimiter
>>> re.sub(r'\A([^:]+:){2}', r'', 'foo:123:bar:baz', count=1)
'bar:baz'
>>> ''.join(re.findall(r'\b\w', 'sea eat car rat eel tea'))
'secret'
# match 'dog' only if it is not preceded by 'parrot'
>>> bool(regex.search(r'(?<!parrot.*)dog', 'fox,cat,dog,parrot'))
True
```

* Using `ruby` syntax highlighting

```ruby
# remove first two columns where : is delimiter
>>> re.sub(r'\A([^:]+:){2}', r'', 'foo:123:bar:baz', count=1)
'bar:baz'
>>> ''.join(re.findall(r'\b\w', 'sea eat car rat eel tea'))
'secret'
# match 'dog' only if it is not preceded by 'parrot'
>>> bool(regex.search(r'(?<!parrot.*)dog', 'fox,cat,dog,parrot'))
True
```

# Bullets

* fruit
    * apple
    * mango
    * grape
        * green
        * black seedless
* pet
    * cat
    * dog
    * parrot

## Picture

![Picture](images/figure1.jpg)

# Conclusion

This sample file helps you see a demo for `markdown` to `pdf` conversion using `pandoc`.
