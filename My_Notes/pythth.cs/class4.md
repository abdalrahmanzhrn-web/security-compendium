# class4

```python
import requests

class parent:
    def __init__(self):
        print("parent")

    def sum(self):
        print("is sum")

class child(parent):
    def __init__(self):
        super().__init__()
        self.sum()

obj=child()
```
