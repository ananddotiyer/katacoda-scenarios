As an extension to this problem, if you had a list of lists as below,

```python
list2d = [[1,2,3],[4,5,6], [7], [8,9]]
```

you could extend them inline using itertools.

Consider the following snippet, as an example.

<pre class="file" data-filename="app.py" data-target="replace">
import itertools
list2d = [[1,2,3],[4,5,6], [7], [8,9]]
merged = list(itertools.chain.from_iterable(list2d))
print(merged)
</pre>

Now, run this by exiting from the Python shell.

To run, `python3 app.py`{{execute}}

However, if you were to use conventional methods, you would use it like so

<pre class="file" data-filename="app.py" data-target="replace">
list2d = [[1,2,3], [4,5,6], [7], [8,9]]
def from_iterable(iterables):
    for it in iterables:
        for element in it:
            yield element


print(list(from_iterable(list2d)))
</pre>

To run, `python3 app.py`{{execute}}

In both the cases above, it flattens the list of lists.
