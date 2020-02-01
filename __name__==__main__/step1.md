When Python reads a .py file, it will initially set its \_\_**name**\_\_ variable and then executes all code in the file.

Suppose you have saved your code in  *myfile.py*.

<pre class="file" data-filename="myfile.py" data-target="replace">
import anotherfile

print(f"__name__: {globals()['__name__']}") # prints "__main__"
</pre>

When you are running  *myfile.py* , it assigns \_\_**main**\_\_ to its \_\_**name**\_\_ variable. It is as if the Python interpreter inserts this at the top of  *myfile.py* , when run as the main program.

\_\_name\_\_ = "\_\_main\_\_"

Here is the contents of *anotherfile.py*.

<pre class="file" data-filename="anotherfile.py" data-target="replace">
print("Hello")

print(f"__name__: {globals()['__name__']}") # prints "anotherfile" when myfile.py is run, "__main__" when anotherfile.py is run.

if __name__ == "__main__":
	print(f"__name__: {globals()['__name__']}")  # prints "__main__" in both cases.
	print("Hello again")
</pre>

When *anotherfile.py* gets imported into *myfile.py*, it assigns "myfile" to the former's  \_\_**name** \_\_ variable. It is as if the Python interpreter inserts this at the top of  *anotherfile.py*.  This happens only when *myfile.py* is run.

\_\_name\_\_ = "myfile"

Instead, when you are running *anotherfile.py*, it assigns \_\_**main**\_\_ to its \_\_**name**\_\_ variable.

Thus, when  *anotherfile.py*  contains the line

if \_\_name\_\_ == "\_\_main\_\_"

contents of the *if* condition gets executed only when  *anotherfile.py*  is run, and not when  *mainfile.py*  is run.

Let's get to a demonstration.  Make sure that contents of both files have been "copied to the editor".

First, execute *anotherfile.py*.

`python anotherfile.py`{{execute}}

Notice that it prints **\__main__** twice, 
- the first time due to line 3, and
- the second time due to line 6 (when run as the the main program)

Now, execute *myfile.py*.

`python myfile.py`{{execute}}

Notice that this time, it prints
- **anotherfile** due to the line 3 of anotherfile.py and 
- **\__main__** due to line 3 of myfile.py.

Enter the python shell, if you wish to practice on the shell.

`python3`{{execute}}

Exit the shell, if you wish to return to experimenting with the files again.

`exit()`{{execute}}