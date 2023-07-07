# django-custon-user

Django provides a built-in authentication system that you can use to handle user authentication and authorization in your web applications. The `AbstractUser` class is a model provided by Django that you can subclass to create a custom user model with additional fields and methods.

When you create a Django project, Django automatically sets up a default user model called `User`. However, if you need to add extra fields or functionalities to the user model, it's recommended to create a custom user model by subclassing `AbstractUser`.

To learn more about `AbstractUser` and how to use it, follow these steps:

1. Create a Django project and navigate to the project directory.
2. Open the file `settings.py` in your project directory and locate the `AUTH_USER_MODEL` setting. If it's not there, you can add it to the file. Set the value of `AUTH_USER_MODEL` to your custom user model, which will be in the format `yourapp.CustomUser`. Replace `yourapp` with the name of your Django app and `CustomUser` with the name of your custom user model.
3. Create a new file, let's say `models.py`, in your app directory (`yourapp`) and open it.
4. Import the necessary Django modules by adding the following lines at the top of the file:
   ```python
   from django.contrib.auth.models import AbstractUser
   from django.db import models
   ```
5. Define your custom user model by subclassing `AbstractUser` and adding any additional fields you need. Here's an example of a custom user model with an extra `birth_date` field:
   ```python
   class CustomUser(AbstractUser):
       birth_date = models.DateField(null=True, blank=True)
   ```
   In this example, we've added a `birth_date` field of type `DateField` to the `CustomUser` model. You can add any additional fields you require.
6. Save the `models.py` file.
7. Run the following command to create and apply the migrations for your custom user model:
   ```
   python manage.py makemigrations
   python manage.py migrate
   ```
   This will create the necessary database tables for your custom user model.
8. Update any existing references to the default `User` model in your code to use your custom user model (`CustomUser` in the example). This includes views, forms, and any other parts of your application that interact with the user model.
9. You can now use your custom user model throughout your Django project. For example, you can create and authenticate users as you would with the default `User` model.

By subclassing `AbstractUser`, you inherit all the fields and methods provided by Django's default user model, such as username, email, password, etc. You can then customize the user model by adding more fields or overriding existing methods to fit your application's needs.

Remember to refer to the Django documentation for more information on the available fields and methods of `AbstractUser` and how to use them effectively in your Django project.

