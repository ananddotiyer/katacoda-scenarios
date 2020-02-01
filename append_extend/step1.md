As the name indicates, *append* appends to the end of a given list.

Let's see an example.

`a = [1, 2, 3]`{{execute}}

Following appends 4 to the list *a*.

`a.append(4)
print(a)`{{execute}}

*extend* adds individual items from a given iterable to the original list.  The iterable can be a list, dictionary, set or tuple.

If you had multiple items to *append*, you will have to use it within a loop.  Thus,

<pre class="file" data-filename="app.py" data-target="replace">
a = [1, 2, 3]
b = [4, 5]
for each in b:
	a.append(each)

print(a)
</pre>

Now, run this by exiting from the Python shell.

To run, `python3 app.py`{{execute}}

or, use the extend method instead.  Ensure, you're in the shell once again,before you continue `python`{{execute}}

`a = [1, 2, 3]
b = [4, 5]
a.extend(b)
print(a)`{{execute}}

*extend* could be used, even when b is a set, or a tuple or a dictionary.  For example,

`a = [1, 2, 3]
b = (4, 5)
a.extend(b)
print(a)`{{execute}}

This also works.

`a = [1, 2, 3]
b = {4: 'Four', 5: 'Five')
a.extend(b)
print(a)`{{execute}}

In the last case, note that the dictionary keys gets added to the original list *a*.
