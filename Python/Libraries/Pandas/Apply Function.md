### Arguments
When adding arguments to the apply function, use the keyword argument of the function. Example:
```python
df.apply(remove_excel_emp, axis=1, user=request.session['ldap_name'])
```