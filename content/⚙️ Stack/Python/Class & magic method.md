---
title: 
tags:
  - python
---

- class
    - make a class and instance

        ```
        # make a rectangle
        # self parameter is always used, because it refers to the initalized object itself
        class rectangle:
            def __init__(self, a, b):
                self.side1=a
                self.side2=b

        		def area(self):
        		        a=self.side1 * self.side2
        		        print("area=",a)

        >>> r1=rectangle(10, 20) #make an instance by calling the class like calling the function
        >>> r1.area()
        area=200
        ```

    - magic method
        - __init__()
            - Constructor, call when an instance is initialized (what’s why always used define parameter!)
        - __new__()
            - do somethings before initialize the object

            ```python
            class Employee:

                def __init__(self):
                    print ("__init__ magic method is called")

                def __new__(random):
                    print ("__new__ magic method is called")
                    inst = object.__new__(random)
                    return inst

            emp = Employee()
            ```

        - __str__()
            - returned class object which is represented as a designed string

            ```python
            #WITHOUT the **str**() function:
            class Person:
              def __init__(self, name, age):
                self.name = name
                self.age = age

            p1 = Person("John", 36)
            print(p1)    # result: <__main__.Person object at 0x2b2a41db3100>

            #WITHOUT the **str**() function:
            class Person:
              def __init__(self, name, age):
                self.name = name
                self.age = age

              def __str__(self):
                return f"{self.name}({self.age})"

            p1 = Person("John", 36)
            print(p1)     # result: John(36)
            ```

        - __del__()
            - Destructor, call when an instance is deleted

            ```python
            class Example:
            # Initializing
                def __init__(self):
                    print("Example Instance.")

            # Calling destructor
                def __del__(self):
                    print("Destructor called, Example deleted.")

            obj = Example()
            del obj
            ```

    - **Inheritance**
        - make a child class

            ```
            class parent_name:
                statements

            class child_name(parent_name):
                statements
            ```

        - Pass the parameter of child class to the parent using super() function

            ```
            #make a rectangle class from quadriLateral class, where attributes of the rectangle can be applied to quadriLateral

            class quadriLateral:
                def __init__(self, a, b, c, d):
                    self.side1=a
                    self.side2=b
                    self.side3=c
                    self.side4=d

            		def perimeter(self):
            		        p=self.side1 + self.side2 + self.side3 + self.side4
            		        print("perimeter=",p)

            class rectangle(quadriLateral):
                def __init__(self, a, b):
                    super().__init__(a, b, a, b)

            >>> r1=rectangle(10, 20)
            >>> r1.perimeter()
            perimeter=60
            ```

        - **Overriding (modify the functionality of the parent)**

            ```
            class rectangle(QuadriLateral):
                def __init__(self, a,b):
                    super().__init__(a, b, a, b)

                def area(self):
                    a = self.side1 * self.side2
                    print("area of rectangle=", a)

            #tranform a rectangle class into a square class

            class square(rectangle):
                def __init__(self, a):
                    super().__init__(a, a)

                def area(self):  #define a function of which the name is the same as parent (overrided)
                    a=pow(self.side1, 2)
                    print('Area of Square: ', a)

            >>>s=Square(10)
            >>>s.area()
            Area of Square: 100
            ```


- parenthesis on function and class
    - With parenthesis: call the function
    - Without parenthesis: reference **the function (point it to a variable)

