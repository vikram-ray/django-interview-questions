# django-interview-questions

- What is class based views and its advangages?
>>> Class-based views provide an alternative way to implement views as Python objects instead of functions. They do not replace function-based views, but have certain differences and advantages when compared to function-based views:
  `Organization of code related to specific HTTP methods (GET, POST, etc.) can be addressed by separate methods instead of conditional branching.`
  `Object oriented techniques such as mixins (multiple inheritance) can be used to factor code into reusable components.`


# django-rest-framework-interview-questions
### Viewsets
- REST framework provides an `APIView` class, which subclasses Django's `View` class. [DOCS](https://www.django-rest-framework.org/api-guide/views/)
```
from rest_framework.views import APIView
from rest_framework.response import Response
from rest_framework import authentication, permissions
from django.contrib.auth.models import User

class ListUsers(APIView):
    """
    View to list all users in the system.

    * Requires token authentication.
    * Only admin users are able to access this view.
    """
    authentication_classes = [authentication.TokenAuthentication]
    permission_classes = [permissions.IsAdminUser]

    def get(self, request, format=None):
        """
        Return a list of all users.
        """
        usernames = [user.username for user in User.objects.all()]
        return Response(usernames)
```
`The view return browsable response or just JSON response based on request. In browser it will show the class-docs defined in comment after class defination`
`Currently out View can only accept GET call. We can extend it by add more class-method .get(), .post(), put(), patch() and .delete()`

