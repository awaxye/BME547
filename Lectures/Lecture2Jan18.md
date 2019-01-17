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

Other styles exist such as google style.  Also have syntax checkers to run.

Define 'main' - description without algorithmic function

```

   def main():
```

Define subfunctions
       add_two()
       subtract_two()
       multiply_two()
       
**style to use verbs for functions
       
 Now work functions.
 
 def add_two(), etc.
 
 placeholders with comments (""")
 
 Docstring indicated for comments but also to assemble documentations later on.

For example, :param v1: number one, :param v2: number 2, :returns: product number

using colons is shorthand for docstring to indicate a variable

**key for medical software

This approach ensures documentation is generated at the same time as code and not a document constructed later.

add info to def of sub function (v1,v2)

Now add an if statement 

```

if __name__ == "__main__":

```

double underscore, internal python variable that is protected.  Shouldn't mess with it.

conditional statement says that if I'm running the proram called main, then this true

then call the main function.  


