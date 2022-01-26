---
layout: post
title: SOLID Principles
tag: Programming
---

**SOLID** is a set of object oriented programming principles that helps make code more maintainable and flexible. The term was coined by 'Uncle Bob' Martin in 2000, who is also famous for 'Clean Code'. These principles can be applied to any object oriented language.

Note: Python does not have inherent interfaces, so I have used Metaclasses to illustrate how interfaces work in Python.

SOLID stands for 5 principles:
1. Single Responsibility Principle
2. Open/Closed Principle
3. Liskov Substitution Principle
4. Interface Segregation Principle
5. Dependency Inversion Principle

## Single Responsibility Principle
> A class should have a single responsibility, meaning it should only have one reason to change.

Looking at the following example of a `FacebookUser` class, it has several functionalities such as adding friends, adding posts, and login.

```python
class SNSUser:
    _friends = []
    _posts = []
    _logged_in = False


    def __init__(self, userName, SNSName):
        self._name = name
        self._sns_name = SNSName # 'facebook', 'instagram'

    def addFriend(newFriend):
        if self._sns_name = "Facebook":
            if newFriend not in self.__friends and len(self.__friends < 1000):
                self.__friends.append(newFriend)
        if self._sns_name = "Instagram":
            if newFriend not in self.__friends and len(self.__friends < 100000000):
                self.__friends.append(newFriend)

    def addPost(content):
        self.__posts.append(content)
    
    def LoginUser(self):
        # Login logic...
        self._logged_in = True
```
The class is responsible for logging in the user, which might seem like a good idea. But what happens if we want to change the loging logic, or another type of login method? We would need to modify the class to change the Login method or add another one. *Changing existing code should be stayed away from as much as possible*, and instead, code should be constructed in an extensible manner.

A better approach thus is to separate the login methods as a separate class that handles all login logic.

```python
class LoginHandler():
    def login_user_with_password(user: User):
        return some_login_method(user)
    
    def login_user_with_fingerprint(user: User):
        return finger_login(user)
```
When login logic changes or another method needs to be added, only this class needs to be modified, reducing the risk of bugs.

## Open/Closed Principle
> Classes should be open for extension, but closed for modification.

This means classes should be *extended* to change functionality, instead of being modified.

If we look at the previous code example, we can see that the `SNSUser` class handles both Facebook and Instagram users in its logic.

```python
class SNSUser:
    #...

    def addFriend(newFriend):
        if self._sns_name = "Facebook":
            if newFriend not in self.__friends and len(self.__friends < 1000):
                self.__friends.append(newFriend)
        if self._sns_name = "Instagram":
            if newFriend not in self.__friends and len(self.__friends < 100000000):
                self.__friends.append(newFriend)
    #...
```
The class is checking if the current User's SNS type is Facebook or Instagram, and adding friends accordingly.

The problem with this setup is that we are only restricted to Facebook and Instagram user, and if we were to add any other type of SNS, we would need to change the code to add another `if` statement. This makes the code not extensible and prone to bugs.

The correct way to fix this problem is to separate out different user classes that inherit from a common `SNSUser` interface. The different classes will each have their own `addFriend` logic.

```python
class SNSUserMeta(type):
    def __instancecheck__(self, instance):
        return self.__subclasscheck__(type(instance))

    def __subclasscheck__(self, subclass):
        return (hasattr(subclass, 'friends') and callable(subclass.addFriend))

class SNSUserInterface(metaclass=SNSUserMeta):
    pass


class FacebookUser(SNSUserInterface):
    _friends = []
    _posts = []
    _logged_in = False


    def __init__(self, userName):
        self._name = name

    def addFriend(newFriend):
          if newFriend not in self._friends and len(self._friends < 1000):
                self._friends.append(newFriend)

    def addPost(content):
        self._posts.append(content)


class InstagramUser(SNSUserInterface):
    _followers_ = []
    _posts = []
    _logged_in = False


    def __init__(self, userName):
        self._name = name

    def addFriend(newFriend):
        if newFriend not in self._followers and len(self._followers < 100000000):
            self._friends.append(newFriend)

```
Now, if the company adds another SNS service e.g. Twitter, instead of modifying the original code, it can just extend the interface and implement its own 'addFriend' logic.

And programs who uses the `addFriend` method would just be able to call the method, without caring about the specific SNS type of logic.

For example, if a brand marketer SNS account wants to add friends through both Facebook and Instgram for marketing purposes, they can get all users from both Facebook and Instagram (who have accepted marketing promotions) and call their `addFriend` method.

```python
class BrandMarketingUser(SNSMarketingUser):
    _users = get_all_users_for_marketing() # get all users from Facebook and Instagram who accepted marketing

    def addUsersForMarketing(self):
        for user in self._users:
            user.addFriend(self)
```

## Liskov Substitution Principle
> Objects should be replaceable by their subtypes without altering how the program works.

This means that subclasses should be completely substitutable for their parent class without breaking the code.

Let's say a new class for `TwitterUser` was created as below.

```python
class TwitterUser(SNSUserInterface):
    _followers_ = []
    _tweets = []
    _logged_in = False


    def __init__(self, name, country):
        self._name = name
        self._country = country # NEW!

    def getCountry():
        return self._country

    def addFriend(newFriend):
        if newFriend not in self._followers and len(self._followers < 100000000):
            self._friends.append(newFriend)
```
Say for example, the legal requirements of Twitter does not allow users from Korea to accept marketing promotions.

If we add the following code to reflect this logic, it will break the program as Facebook and Instagram classes do not have a country property.

```python
class BrandMarketingUser(SNSMarketingUser):
    _users = get_all_users_for_marketing() # get all users from Facebook and Instagram who accepted marketing

    def addUsersForMarketing(self):
        for user in self._users:
            country = user.getCountry() # error!
            if country != 'Korea':
                user.addFriend(self)
```
Changing Facebook and Instagram classes to add the country property is also not a good idea.

A better approach would be to separate out the `BrandMarketingUser` class depending on whether country is required for checking.

```python
class BrandMarketingUser(SNSMarketingUser):
    _users = get_all_users_for_marketing() # get all users from Facebook and Instagram

    def addUsersForMarketing(self):
        for user in self._users:
            user.addFriend(self)

class BrandMarketingUserCheckCountry(SNSMarketingUser):
    _users = get_all_users_for_marketing_country() # get twitter accounts

    def addUsersForMarketing(self):
        for user in self._users:
            if country != 'Korea':
                user.addFriend(self)
```