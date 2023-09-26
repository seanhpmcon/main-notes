#databases #sql #datatypes
The following code converts the pandas nulls type to python None type:
```python
df.fillna(np.nan).replace([np.nan], [None])
```

The first `fillna` will replace all of (None, NAT, np.nan, etc) with Numpy's NaN, then replace Numpy's NaN with python's None.