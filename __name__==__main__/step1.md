## Task

### myfile.py
<pre class="file" data-filename="myfile.py" data-target="replace">
import anotherfile

print(f"__name__: {globals()['__name__']}") # prints "__main__"
</pre>

### anotherfile.py
<pre class="file" data-filename="anotherfile.py" data-target="replace">
print("Hello")

print(f"__name__: {globals()['__name__']}") # prints "anotherfile" when myfile.py is run, "__main__" when anotherfile.py is run.

if __name__ == "__main__":
	print(f"__name__: {globals()['__name__']}")  # prints "__main__" in both cases.
	print("Hello again")
</pre>

First, execute anotherfile.py.

`python anotherfile.py`{{execute}}

Notice that it prints **__main__** twice, the first time due to line-3, and second time due to line-6 (when run as the the main program)

Now, execute myfile.py.

`python myfile.py`{{execute}}

Notice that this time, it prints **anotherfile** due to the line-3 of anotherfile.py, and **__main__** due to line-3 of myfile.py.


