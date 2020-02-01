As the name indicates, *append* appends to the end of a given list.

Let's see an example.

`a = [1, 2, 3]`{{execute}}

Following appends 4 to the list *a*.

`a.append(4)`{{execute}}

*extend* adds individual items from a given iterable to the original list.  The iterable can be a list, dictionary, set or tuple.

If you had multiple items to *append*, you will have to use it within a loop.  Thus,

`a = [1, 2, 3]
b = [4, 5]
# a.append(b)  # will not work
for each in b:
	a.append(each)`{{execute}}

or, use the extend method instead.

`a = [1, 2, 3]
b = [4, 5]
a.extend(b)`{{execute}}

*extend* could be used, even when b is a set, or a tuple or a dictionary.  For example,

`a = [1, 2, 3]
b = (4, 5)
a.extend(b)`{{execute}}

This also works.

`a = [1, 2, 3]
b = {4: 'Four', 5: 'Five')
a.extend(b)`{{execute}}

In the last case, note that the dictionary keys gets added to the original list *a*.

# Step2

*append* and *extend* mutates the original list.  To demonstrate this, consider the following snippet.

`a = [1, 2, 3]
b = [4, 5]
orig_address = id(a)
a.append(4)
append_address = id(a)
a.extend(b)
extend_address = id(a)

orig_address == append_address == extend_address  # returns True indicating that all objects point to the same memory location`{{execute}}

Now, what about *adding* two lists using '+' operator.  Is that different from *extend*?  Let us see.

`a = [1, 2, 3]
b = [4, 5]
orig_address = id(a)
a = a + b
print(a)  # output is identical to that from extend

add_address = id(a)
add_address == orig_address  # return False, indicating that it creates a new list.`{{execute}}

However, if you use += shorthand notation, it'll mutate the original list instead.

`a = [1, 2, 3]
b = [4, 5]
orig_address = id(a)
a += b
print(a)  # output is identical to that from extend

add_address = id(a)
add_address == orig_address  # return True, indicating that the original list is mutated.

As an interesting sidenote, if you extend a list with a string, it'll add the individual characters of the string to the original list.  This is because a string is treated as a list/sequence of characters.

# Step3

Let's see how *extend* compares to append, in terms of performance.  We'll use the *timeit* module to measure the time it takes to perform the operation, a specified number of times (defaults to 3).

Refer to [the documentation](https://docs.python.org/2/library/timeit.html) for details about how timeit.repeat works.

`def append(alist, iterable):
    for item in iterable:
        alist.append(item)

def extend(alist, iterable):
    alist.extend(iterable)`{{execute}}
	
`min(timeit.repeat(lambda: append([], "abcdefghijklmnopqrstuvwxyz")))`{{execute}}

`min(timeit.repeat(lambda: extend([], "abcdefghijklmnopqrstuvwxyz")))`{{execute}}

This shows that *extend* is faster than *append*.  THis is true as far there's at least one element to add.  If there's a single element to add to the list, *extend* if marginally slower, and hence it's recommended to use *append* in such cases.  

#Step4

As an extension to this problem, if you had a list of lists as below,

'''python
list2d = [[1,2,3],[4,5,6], [7], [8,9]]
'''

you could extend them inline using itertools.

Consider the following snippet, as an example.

`import itertools
list2d = [[1,2,3],[4,5,6], [7], [8,9]]
merged = list(itertools.chain.from_iterable(list2d))
print(merged)  # flattens the list of lists`{{execute}}

However, if you were to use conventional methods, you would use it like so

`list2d = [[1,2,3], [4,5,6], [7], [8,9]]
def from_iterable(iterables):
    for it in iterables:
        for element in it:
            yield element

list(from_iterable(list2d))  # flattens the list of lists`{{execute}}
