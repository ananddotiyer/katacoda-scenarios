When \* and \*\* is used on the left side of the assignment operator, it's termed extended iterable unpacking.

`first, *rest = [1,2,3,4]`{{execute}}

`first, *l, last = [1,2,3,4]`{{execute}}

Introduced into Python 3 is a feature wherein, function parameters accept only keyword arguments, and not positional arguments.

<pre class="file" data-filename="app.py" data-target="replace">
def foo(a, b, name, age, salary):
    print(a, name)

numbers = [1, 2, 3, 4, 5]
employee = {'name': 'one', 'age': 27, 'salary': 10000}
foo(*numbers)
</pre>

Now, exit from the Python shell before running this `exit()
python3 app.py`{{execute}}

In this example, all 5 items in the *numbers* list are unpacked and used as function parameters.

Now, let's see what happens when you supplied the \*employee\* dict as keyword arguments.

<pre class="file" data-filename="app.py" data-target="replace">
def foo(a, b, name, age, salary):
    print(a, name)

numbers = [1, 2, 3, 4, 5]
employee = {'name': 'one', 'age': 27, 'salary': 10000}
foo(*numbers, **employee)
</pre>

To run, `python3 app.py`{{execute}}

Contrary to what is expected, this results in *TypeError: foo() got multiple values for argument 'name'*

What just happened?  The call unpacked both positional and keyword arguments, and using up for the function parameters.  Obviously, this isn't what you wanted.

We'll solve this by using "keyword-only" arguments: arguments that can only be supplied by keyword and which will never be automatically filled in by a positional argument.

<pre class="file" data-filename="app.py" data-target="replace">
def foo(a, b, *, name, age, salary):
    print(a, name)

numbers = [1, 2, 3, 4, 5]
employee = {'name': 'one', 'age': 27, 'salary': 10000}
foo(*numbers, **employee)
</pre>

Note the *\** used as the third parameter in the funtion *foo*.  Any parameters after *\** are required to be keyword-only arguments.

To run, `python3 app.py`{{execute}}

will now result in *TypeError: foo() takes 2 positional arguments but 5 positional arguments (and 3 keyword-only arguments) were given*, as expected.

Following is an example, where exactly two positional arguments are used, before keyword-only arguments.  In this case, it would work as expected.

<pre class="file" data-filename="app.py" data-target="replace">
def foo(a, b, *, name, age, salary):
    print(a, name)

numbers = [1, 2]
employee = {'name': 'one', 'age': 27, 'salary': 10000}
foo(*numbers, **employee)
</pre>

To run, `python3 app.py`{{execute}}