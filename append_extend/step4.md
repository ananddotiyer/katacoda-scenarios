As an extension to this problem, if you had a list of lists as below,

```python
list2d = [[1,2,3],[4,5,6], [7], [8,9]]
```

you could extend them inline using itertools.

Consider the following snippet, as an example.

`import itertools
list2d = [[1,2,3],[4,5,6], [7], [8,9]]
merged = list(itertools.chain.from_iterable(list2d))
print(merged)`{{execute}}

However, if you were to use conventional methods, you would use it like so

`list2d = [[1,2,3], [4,5,6], [7], [8,9]]
def from_iterable(iterables):
    for it in iterables:
        for element in it:
            yield element

print(list(from_iterable(list2d)))`{{execute}}

In both the cases above, it flattens the list of lists.
