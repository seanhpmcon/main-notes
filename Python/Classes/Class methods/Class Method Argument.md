The first argument of a classmethod method is the class itself (cls) and not the instance of the class (this):
```python
class A(B): 
    # Omitted bulk of irrelevant code in the class

    def __init__(self, uid=None):
        self.uid = str(uid)

    @classmethod
    def get(cls, uid):
        o = cls(uid)
        # Also Omitted lots of code here
```

From stack overflow commenter, `o = cls(uid)` is the same as `o = A(uid)`.