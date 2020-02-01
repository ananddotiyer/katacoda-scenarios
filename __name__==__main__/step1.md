When Python reads a .py file, it will initially set its \_\_ **name** \_\_ variable and then executes all code in the file.

Suppose you have saved your code in  **myfile.py**.

### myfile.py
<pre class="file" data-filename="myfile.py" data-target="replace">
import anotherfile

print(f"__name__: {globals()['__name__']}") # prints "__main__"
</pre>

When you are running  **myfile.py** , it assigns \_\_ **main** \_\_ to its \_\_ **name** \_\_ variable. It is as if the Python interpreter inserts this at the top of  **myfile.py** , when run as the main program.

\_\_ **name** \_\_ = "\_\_ **main** \_\_"

Here is the contents of anotherfile.py.

### anotherfile.py
<pre class="file" data-filename="anotherfile.py" data-target="replace">
print("Hello")

print(f"__name__: {globals()['__name__']}") # prints "anotherfile" when myfile.py is run, "__main__" when anotherfile.py is run.

if __name__ == "__main__":
	print(f"__name__: {globals()['__name__']}")  # prints "__main__" in both cases.
	print("Hello again")
</pre>

When **anotherfile.py** gets imported into **myfile.py**, it assigns "myfile" to the former's  \_\_ **name** \_\_ variable. It is as if the Python interpreter inserts this at the top of  **anotherfile.py**  when it is imported from  **mainfile.py**.

\_\_ **name** \_\_  = "myfile"

Thus, when  **anotherfile.py**  contains the line

if \_\_ **name** \_\_ == "\_\_ **main** \_\_"

contents of the _if _condition gets executed only when  **anotherfile.py**  is run, and not when  **mainfile.py**  is run.

Let's get to a demonstration.

First, execute **anotherfile.py**.

`python anotherfile.py`{{execute}}

Notice that it prints **\__main__** twice, 
- the first time due to line 3, and
- the second time due to line 6 (when run as the the main program)

Now, execute **myfile.py**.

`python myfile.py`{{execute}}

Notice that this time, it prints
- **anotherfile** due to the line 3 of anotherfile.py and 
- **\__main__** due to line 3 of myfile.py.

Enter the python shell, if you wish to practice on the shell.

`python3`{{execute}}

Exit the shell, if you wish to return to experimenting with the files again.

`exit()`{{execute}}