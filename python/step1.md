`class Pair(object):
    def __init__(self, x, y):
        self.x = x
        self.y = y
    def __repr__(self):
        return 'Pair({0.x!r}, {0.y!r})'.format(self)
    def __str__(self):
        return '({0.x!s}, {0.y!s})'.format(self)`{{execute}}
        
<pre class="file" data-filename="app.py" data-target="replace">
    console.log("app.py here...")
</pre>

```python
a = 'anand'
print()
```
