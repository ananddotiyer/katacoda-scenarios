The \*args and \*\*kwargs can be used to allow an arbitrary number of arguments to functions.  For more details on this, refer to [Python documentation](http://docs.python.org/dev/tutorial/controlflow.html#more-on-defining-functions)

\*args will give you all function parameters as a tuple.

<pre class="file" data-filename="app.py" data-target="replace">
def numbers(*args):
    for a in args:
        print(a)
</pre>

To run, `python3 app.py`{{execute}}

Ensure, you're in the shell,before you continue.  `python`{{execute}}

Now, call the function as

`numbers(1)`{{execute}}

and

`numbers(1,2,3)`{{execute}}

Note that the function prints any number of arguments passed into it.

\*\*kwargs will give you all keyword arguments as a dictionary.

<pre class="file" data-filename="app.py" data-target="replace">
def employee(**kwargs):
    for a in kwargs:
        print(a, kwargs[a])
</pre>

Now, exit from the Python shell before running this `exit()
python3 app.py`{{execute}}

Ensure, you're in the shell,before you continue.  `python`{{execute}}

Now, call the function as

`employee(name='one')`{{execute}}

and

`employee(name='one', age=27, salary=10000)`{{execute}}

In both cases, we can also use normal arguments to allow a set of fixed and some variable arguments.

<pre class="file" data-filename="app.py" data-target="replace">
def employee(*args, **kwargs):
	print (args)
	print (kwargs)
</pre>

Now, exit from the Python shell before running this `exit()
python3 app.py`{{execute}}

Ensure, you're in the shell,before you continue.  `python`{{execute}}

Now, call the function as

`employee(1, name='one')`{{execute}}

and

`employee(1, 2, name='one', age=27)`{{execute}}