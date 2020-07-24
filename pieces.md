1. get_FOO_display()

For each model field that has choices set, Django will add a method to retrieve the human-readable name for the field’s current value. See get_FOO_display() in the database API documentation.

2. Generic views related

Important: The generic class-based detail view expects to be passed a parameter named pk. If you're writing your own function view you can use whatever parameter name you like, or indeed pass the information in an unnamed argument.

3. Session related saving process

If you're updating some information within session data, then Django will not recognise that you've made a change to the session and save the data (for example, if you were to change "wheels" data inside your "my_car" data, as shown below). In this case you will need to explicitly mark the session as having been modified.
 
(Similar to mongodb in express, mark the data that has been changed.)
