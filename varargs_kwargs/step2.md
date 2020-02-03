\*args and \*kwargs can also be used when calling functions too.  This is termed as unpacking of argument lists.

<pre class="file" data-filename="app.py" data-target="replace">
def foo(a, b, name, age, salary):
    print(a, name)

numbers = [1, 2]
employee = {'name': 'one', 'age': 27, 'salary': 10000}

foo(*numbers, **employee)  # prints 1, 'one'
</pre>

To run, `python3 app.py`{{execute}}

Note that upon calling the function it unpacks both iterables, and uses them as appropriate.

In this example, it prints the first item in the *numbers* list and *name* from the *employee* dict.

The keys in *employee* have to be named exactly like the parameters of function foo. Otherwise it will throw a *TypeError*.

<pre class="file" data-filename="app.py" data-target="replace">
def foo(a, b, name, age, salary):
    print(a, name)

mydict = {'x':1,'y':2,'z':3,'badnews':9}  # TypeError
foo(**mydict)
</pre>

To run, `python3 app.py`{{execute}}

Ensure, you're in the shell,before you continue.  `python3`{{execute}}

As another example, we can use dict expansion in str.format

`foo = 'FOO'
bar = 'BAR'
'this is foo, {foo} and bar, {bar}'.format(**locals())`{{execute}}

Note, **locals() refers to a dictionary containing all local variables.

\* can also unpack a generator.

`x = [1, 2, 3]
y = [4, 5, 6]
unzip_x, unzip_y = zip(*zip(x, y))
print(unzip_x)
print(unzip_y)`{{execute}}

It prints (1, 2, 3) for unzip_x and (4, 5, 6) for unzip_y.  

This is because, the inner zip will generate tuples (1, 4), (2, 5), (3, 6).
