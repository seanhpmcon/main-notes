#fileupload #forms
When using forms to do file uploads in django, you have to pass two parameters, one for the uploaded file and another for the form data. Also, in the html form tag, add an attribute `enctype` and set it to `"multipart/form-data"` .

Example:
```python
f = ContactFormWithFile(request.POST, request.FILES)
```