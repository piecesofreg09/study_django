1. get_FOO_display()

For each model field that has choices set, Django will add a method to retrieve the human-readable name for the field’s current value. See get_FOO_display() in the database API documentation.

2. Generic views related

Important: The generic class-based detail view expects to be passed a parameter named pk. If you're writing your own function view you can use whatever parameter name you like, or indeed pass the information in an unnamed argument.

3. Session related saving process

If you're updating some information within session data, then Django will not recognise that you've made a change to the session and save the data (for example, if you were to change "wheels" data inside your "my_car" data, as shown below). In this case you will need to explicitly mark the session as having been modified.
 
(Similar to mongodb in express, mark the data that has been changed.)

4. Log in/out page, Authentication

Django provides almost everything you need to create authentication pages to handle login, log out, and password management "out of the box". This includes a URL mapper, views and forms, but it does not include the templates — we have to create our own!

5. Forms

Important: While you can also access the form data directly through the request (for example, request.POST['renewal_date'] or request.GET['renewal_date'] if using a GET request), this is NOT recommended. The cleaned data is sanitized, validated, and converted into Python-friendly types.

6. Forms with customized constructor

https://stackoverflow.com/questions/1941812/django-error-got-multiple-values-for-keyword-argument

Don't use explicitly named keywords argument to pass data
a function signature of `func(a, b=123, *kwargs)` with a call `func(14, b=100)` will result in the variable `b` being passed to the function twice, and invoke `__init__() got multiple values for keyword argument` error.

7. Test related: What to test

You should test all aspects of your own code, but not any libraries or functionality provided as part of Python or Django.

So for example, consider the Author model defined below. You don't need to explicitly test that first_name and last_name have been stored properly as CharField in the database because that is something defined by Django (though of course in practice you will inevitably test this functionality during development). Nor do you need to test that the date_of_birth has been validated to be a date field, because that is again something implemented in Django.

However you should check the text used for the labels (First name, Last name, Date of birth, Died), and the size of the field allocated for the text (100 chars), because these are part of your design and something that could be broken/changed in future.

8. Test with assertions

We can't get the `verbose_name` directly using `author.first_name.verbose_name`, because author.first_name is a string (not a handle to the `first_name` object that we can use to access its properties). Instead we need to use the author's `_meta` attribute to get an instance of the field and use that to query for the additional information.

We chose to use `assertEquals(field_label,'first name')` rather than `assertTrue(field_label == 'first name')`. The reason for this is that if the test fails the output for the former tells you what the label actually was, which makes debugging the problem just a little easier.

9. `__init__.py`

This file makes the directory as a package. Hence you can use `.` notation to access files in this directory.
