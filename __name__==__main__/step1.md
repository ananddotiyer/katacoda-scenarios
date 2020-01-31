## Task

###myfile.py
<pre class="file" data-filename="myfile.py" data-target="replace">
import anotherfile

print(f"__name__: {globals()['__name__']}") # prints "__main__"
</pre>

###anotherfile.py
<pre class="file" data-filename="anotherfile.py" data-target="replace">
print("Hello")

print(f"__name__: {globals()['__name__']}") # prints "anotherfile" when myfile.py is run, "__main__" when anotherfile.py is run.

if __name__ == "__main__":
	print(f"__name__: {globals()['__name__']}")  # prints "__main__" in both cases.
	print("Hello again")
</pre>
