--- 
title: "Python Notes – 8 : Object-Oriented Basics" 
date: '2009-03-27T01:51:00.000-05:00' 
tags: 
    - Python 
modified_time: '2009-05-15T01:55:26.784-05:00' 
blogger_id: tag:blogger.com,1999:blog-59384554657271185.post-4961343029819958668
blogger_orig_url: http://ebeid-soliman.blogspot.com/2009/03/python-notes-8.html 
---

Welcome to our eighth note in our Python learning process. This note
will talk about object oriented features in Python.

#### Classes and Objects

A class definition looks like this:

> class Point:

>     pass

Class definitions can appear anywhere in a program, but they are usually
near the beginning (after the import statements). By creating the Point
class, we created a new type, also called Point. The members of this
type are called instances of the type or objects. Creating a new
instance is called instantiation. To instantiate a Point object, we call
a function named Point:

> &gt;&gt;&gt; blank = Point()

The variable blank is assigned a reference to a new Point object. A
function like Point that creates new objects is called a constructor. If
you tried to get the type of blank, you got instance:

> &gt;&gt;&gt; type(blank)

> &lt;type 'instance'&gt;

If you tried to print blank:

> &gt;&gt;&gt; print blank

> &lt;\_\_main\_\_.point instance at 0x01922AF8&gt;

The result indicates that blank is an instance of the Point class and it
was defined in \_\_main\_\_ . 0x01922AF8 is the unique identifier for
this object, written in hexadecimal (base 16).

#### Attributes

We can add new data to an instance using dot notation:

> &gt;&gt;&gt; blank.x = 3.0

> &gt;&gt;&gt; blank.y = 4.0

These new data items called attributes.

> &gt;&gt;&gt; print blank.y

> 4.0

> &gt;&gt;&gt; x = blank.x

> &gt;&gt;&gt; print x

> 3.0

#### Sameness

To find out if two references refer to the same object, use the ==
operator. For example:

> &gt;&gt;&gt; p1 = Point()

> &gt;&gt;&gt; p1.x = 3

> &gt;&gt;&gt; p1.y = 4

> &gt;&gt;&gt; p2 = Point()

> &gt;&gt;&gt; p2.x = 3

> &gt;&gt;&gt; p2.y = 4

> &gt;&gt;&gt; p1 == p2

> 0

Even though p1 and p2 contain the same coordinates, they are not the
same object. If we assign p1 to p2, then the two variables are aliases
of the same object:

> &gt;&gt;&gt; p2 = p1

> &gt;&gt;&gt; p1 == p2

> 1

This type of equality is called *shallow equality* because it compares
only the references, not the contents of the objects. To compare the
contents of the objects - *deep equality* - we can write our own
function to do that, like that:

> def samePoint(p1, p2) :

>     return (p1.x == p2.x) and (p1.y == p2.y)

Now if we create two different objects that contain the same data, we
can use samePoint to find out if they represent the same point.

> &gt;&gt;&gt; p1 = Point()

> &gt;&gt;&gt; p1.x = 3

> &gt;&gt;&gt; p1.y = 4

> &gt;&gt;&gt; p2 = Point()

> &gt;&gt;&gt; p2.x = 3

> &gt;&gt;&gt; p2.y = 4

> &gt;&gt;&gt; samePoint(p1, p2)

> 1

#### Copying

Aliasing can make a program difficult to read because changes made in
one place might have unexpected effects in another place. Copying an
object is often an alternative to aliasing. The copy module contains a
function called copy that can duplicate any object:

> &gt;&gt;&gt; import copy

> &gt;&gt;&gt; p1 = Point()

> &gt;&gt;&gt; p1.x = 3

> &gt;&gt;&gt; p1.y = 4

> &gt;&gt;&gt; p2 = copy.copy(p1)

> &gt;&gt;&gt; p1 == p2

> 0

> &gt;&gt;&gt; samePoint(p1, p2)

> 1

Copy works fine for objects that doesn't contain any embedded objects.
If the object contains references to other objects, Copy will copy the
embedded references to the destination. This ends up that the both
copies reference the same internal objects.

You can use deepcopy which copies not only the object but also any
embedded objects.

> &gt;&gt;&gt; b2 = copy.deepcopy(b1)

Now b1 and b2 are completely separate objects.

#### The initialization method

The initialization method is a special method that is invoked when an
object is created. The name of this method is \_\_init\_\_.

> class point:

>     def \_\_init\_\_(self, x = 0, y = 0):

>         Self.x = x

>         Slef.y = y

When we invoke the point constructor, the arguments we provide are
passed along to init:

> &gt;&gt;&gt; first = point(5,7)

> &gt;&gt;&gt; first.x

> 5

> &gt;&gt;&gt; first.y

> 7

Because the parameters are optional, we can omit them:

> &gt;&gt;&gt; second = point()

> &gt;&gt;&gt; second.x

> 0

> &gt;&gt;&gt; second.y

> 0

We can also provide a subset of the parameters by naming them
explicitly:

&gt;&gt;&gt; third = point(y=10)

> &gt;&gt;&gt; third.x

> 0

> &gt;&gt;&gt; third.y

> 10

#### The \_\_str\_\_ method

The \_\_str\_\_ method of any class is called by the Python in any
operation that requires the class instance to be converted to string.
Operations like that are print. Syntax like that:

> class xyz:

>     def \_\_str\_\_(self):

>         return "Our class xyz"

> &gt;&gt;&gt; a = xyz()

> &gt;&gt;&gt; a

> &lt;\_\_main\_\_.xyz instance at 0x02627300&gt;

> &gt;&gt;&gt; print y

> Our class xyz

#### Instances as parameters

You can pass an instance as a parameter in the usual way. For example:

> def printPoint(p):

>     print '(' + str(p.x) + ', ' + str(p.y) + ')'

#### Instances as return values

Functions can return instances. For example:

> def sumPoints(A,B)

>     Z = Point ()

>     Z.x = A.x + B.x

>     Z.y = A.y + B.y

>     return Z

#### Operator overloading

Operator overloading means changing the definition and behavior of the
built-in operators when they are applied to user-defined types. For
example, to override the addition operator + , we provide a method named
\_\_add\_\_ in our point class :

> class Point:
>
>     def \_\_add\_\_(self, other):

>         return Point(self.x + other.x, self.y + other.y)

the first parameter is the object on which the method is invoked. The
second parameter is conveniently named other to distinguish it from
self. Now, when we apply the + operator to Point objects, Python invokes
add :

> &gt;&gt;&gt; p1 = Point(3, 4)

> &gt;&gt;&gt; p2 = Point(5, 7)

> &gt;&gt;&gt; p3 = p1 + p2

> &gt;&gt;&gt; print p3

> (8, 11)

The expression p1 + p2 is equivalent to p1. add (p2), but obviously more
elegant. You can change the behavior of many operators through
overloading their respective functions, which are available at
<http://www.python.org/doc/2.2/ref/numeric-types.html>

#### Inheritance

Inheritance is the ability to define a new class that is a modified
version of an existing class. The new class inherits all of the methods
of the existing class. The new class may be called child class or
subclass. The syntax is like:

> class class1(object):

>     K = 7

>     def \_\_init\_\_(self, color='green'):

>         Self.color = color

>     def Hello1(self):

>         Print "Hello from class1"

>     def printColor(self):

>         print "preferred ", self.color

> class class2(class1):

>     def Hello2(self):

>     print "Hello from class2"

>     print self.k

Here class2 is the child of class1.

> &gt;&gt;&gt; c1 = class1('blue')

> &gt;&gt;&gt; c2 = class2('red')

> &gt;&gt;&gt; c1.Hello1()

> Hello from class1

> &gt;&gt;&gt; c2.Hello2()

> Hello from class2

> 7

Child class can access parent class methods

> &gt;&gt;&gt; c2.Hello1()

> Hello from class1
>
> The parent constructor called automatically for Childs, as following:

> &gt;&gt;&gt; c1.printColor()

> preferred blue

> &gt;&gt;&gt; c2.printColor()

> preferred red

You can check for class methods, attributes using hasattr method:

> if hasattr(class1, "Hello2"):

>     print c1.Hello2()

> else:

>     print "Class1 does not contain method Hello2()"
>
> Class1 does not contain method Hello2()

To check the inheritance relation between two class :

> if issubclass(class2, class1)

>      Print "Class2 is a subclass of Class1”

In this note we tried to cover as much as we can of the Python object
oriented features. We give it a more advanced note in the future.
