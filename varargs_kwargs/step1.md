The \*args and \*\*kwargs can be used to allow an arbitrary number of arguments to functions.  For more details on this, refer to [Python documentation](http://docs.python.org/dev/tutorial/controlflow.html#more-on-defining-functions)

\*args will give you all function parameters as a tuple.

<pre class="file" data-filename="app.py" data-target="replace">
def numbers(*args):
    for a in args:
        print(a)
		
numbers(1)  # prints 1

numbers(1,2,3)  # prints 1, 2, 3
</pre>

To run, `python3 app.py`{{execute}}

Note that the function prints any number of arguments passed into it.

\*\*kwargs will give you all keyword arguments as a dictionary.

<pre class="file" data-filename="app.py" data-target="replace">
def employee(**kwargs):
    for a in kwargs:
        print(a, kwargs[a])
		
employee(name='one')  # prints name

employee(name='one', age=27, salary=10000)  # prints name, age, salary
</pre>

To run, `python3 app.py`{{execute}}

Note that *kwargs* include any number of named parameters passed into the function.

In both cases, we can also use normal arguments to allow a set of fixed and some variable arguments.

<pre class="file" data-filename="app.py" data-target="replace">
def employee(*args, **kwargs):
	print (args)
	print (kwargs)
	
employee(1, name='one')  # prints 1 as tuple, name as dict.

employee(1, 2, name='one', age=27)  # print 1 as tuple, name, age as dict.
</pre>

All named parameters fill up for *kwargs*, and the rest fills up for *args*.

To run, `python3 app.py`{{execute}}
