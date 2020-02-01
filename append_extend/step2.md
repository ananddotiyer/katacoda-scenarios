*append* and *extend* mutates the original list.  To demonstrate this, consider the following snippet.

`a = [1, 2, 3]
b = [4, 5]
orig_address = id(a)
a.append(4)
append_address = id(a)
a.extend(b)
extend_address = id(a)

orig_address == append_address == extend_address`{{execute}}

In the above example, it returns True indicating that all objects point to the same memory location

Now, what about *adding* two lists using '+' operator.  Is that different from *extend*?  Let us see.

`a = [1, 2, 3]
b = [4, 5]
orig_address = id(a)
a = a + b
print(a)

add_address = id(a)
add_address == orig_address`{{execute}}

In the example above, it returns False, indicating that it creates a new list.

However, if you use += shorthand notation, it'll mutate the original list instead.

`a = [1, 2, 3]
b = [4, 5]
orig_address = id(a)
a += b
print(a)

add_address = id(a)
add_address == orig_address`{{execute}}

Note that the above code returns True, indicating that the original list is mutated.

As an interesting sidenote, if you extend a list with a string, it'll add the individual characters of the string to the original list.  This is because a string is treated as a list/sequence of characters.

Try this.

`a = ['a', 'b', 'c']
b = "def"
a.extend(b)
print(a)`{{execute}}