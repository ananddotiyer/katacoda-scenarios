Let's see how *extend* compares to append, in terms of performance.  We'll use the *timeit* module to measure the time it takes to perform the operation, a specified number of times (defaults to 3).

Refer to [the documentation](https://docs.python.org/2/library/timeit.html) for details about how timeit.repeat works.

<pre class="file" data-filename="app.py" data-target="replace">
def append(alist, iterable):
    for item in iterable:
        alist.append(item)

def extend(alist, iterable):
    alist.extend(iterable)

import timeit

print(min(timeit.repeat(lambda: append([], "abcdefghijklmnopqrstuvwxyz"))))

print(min(timeit.repeat(lambda: extend([], "abcdefghijklmnopqrstuvwxyz"))))
</pre>

Now, run this by exiting from the Python shell. `exit()`{{execute}}

To run, `python3 app.py`{{execute}}

Ensure, you're in the shell once again,before you continue.  `python`{{execute}}

This shows that *extend* is faster than *append*.  THis is true as far there's at least one element to add.  If there's a single element to add to the list, *extend* if marginally slower, and hence it's recommended to use *append* in such cases.  
