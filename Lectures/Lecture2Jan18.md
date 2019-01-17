# Python Fundamentals

Approach to coding:  sequential, object, state machine, modular

Use a text editor for now, talk about development environments later

Start with simple code -> Modules (collection of functional items)
->Package (bundles of modules) -> Classes (object oriented)

Make a new repository from gitbash (mkdir, cd to new dir, git init)

Vim fun.py

## Python Starter Notes
* Python uses indentation--not semicolons and curly braces--to delineate
  different logical aspects of code.
```
if BOOLEAN_IS_TRUE:
    do_this()
else:
    do_that()
    and_this()

test_tuple = (1, 2, 3)
test_list = ['a', 'b', 'c']

for n, val in enumerate(test_tuple):
    print(val)
    print(n)
    print(test_tuple[n])

```
Not a fixed number of spaces, just have to be consistent.

Let's adopt a style for this course.  

[Pep8](https://www.python.org/dev/peps/pep-0008/ "PEP 8")

Define 'main' - description without algorithmic function
   def main():
   
Note that python uses indentation to indicate 




