---
title: 
tags:
  - python
---
- decorator ([link](https://www.tutorialsteacher.com/python/decorators))
    - construction and apply
        - decorator in Python can be defined over any appropriate function using the `@decorator_function_name`syntax to extend the functionality of the underlying function

            [[Python/Untitled 1.png]]

        - Apply of decorator

            [[Python/Untitled 2.png]]

    - build-in decorator
        - @property
            - a decorator for the [property() function](https://www.tutorialsteacher.com/python/property-function), then what is property()?

                ```python
                #With attrib = property(fget, fset, fdel, doc) inside the class, we have an ability to get, set, del and document the value using the functions we designed

                class person:
                    def __init__(self, name):
                        self.__name=name
                    def getname(self):
                        print('getname() called')
                        return self.__name
                    def setname(self, name):
                        print('setname() called')
                        self.__name=name
                    def delname(self):
                        print('delname() called')
                        del self.__name
                    # Set property to use get_name, set_name
                    # and del_name methods
                    name=property(getname, setname, delname,doc='name of the person')

                p = Person('Stanley')

                # calls the getter
                print(p.name)
                # Prints Getting name: Stanley

                # calls the setter
                p.name = 'Bob'
                # Prints Setting name to Bob

                # calls the deleter
                del p.name
                # Prints Deleting name
                ```

            - How to use the decorator

                ```python
                class Person():
                    def __init__(self, value):
                        self.hidden_name = value

                    @property       # put the property before getting function
                    def name(self):
                        print('Getting name:')
                        return self.hidden_name

                    @name.setter    # use the name of getting function + '.setter' to indicate setting function
                    def name(self, value):
                        print('Setting name to', value)
                        self.hidden_name = value

                    @name.deleter
                    def name(self): # use the name of getting function + '.deleter' to indicate setting function
                        print('Deleting name')
                        del self.hidden_name

                p = Person('Stanley')

                # calls the getter
                print(p.name)
                # Prints Getting name: Stanley

                # calls the setter
                p.name = 'Bob'
                # Prints Setting name to Bob

                # calls the deleter
                del p.name
                # Prints Deleting name
                ```

        - @classmethod
            - a decorator for the [classmethod() function](https://www.tutorialsteacher.com/python/property-function), then what is classmethod()?

                ```python
                #classmethod() declares a class method, if it is not used, the method is belonged to the object
                class student:
                    name = 'John'

                    def show_name(self):
                        print("The student's name is ",self.name)

                student.show_name = classmethod(student.show_name)
                student.show_name()  #output: The student's name is  John
                ```

            - How to use the decorator

                ```python
                #classmethod() declares a class method, if it is not used, the method is belonged to the object

                class student:
                    name = 'John'

                    @classmethod
                    def show_name(cls):   #use cls instead of self, because now we refer it to the current class
                        print("The student's name is ",cls.name)

                student.show_name()  #output: The student's name is John
                ```

        - @staticmethod

            ```python
            #static method = without referencing any object/ parameters, itself stands alone
            #Declares a static method in the class, which cannot have cls or self parameter/attributes.
            #The static method can be called using ClassName.MethodName() and also using object.MethodName().
            #It can return an object of the class.

            class Student:
                name = 'unknown' # class attribute

                def __init__(self):
                    self.age = 20  # instance attribute

                @staticmethod
                def tostring():
                    print('Student Class')

            #call from class
            >>> Student.tostring()  # output: 'Student Class'
            #call from object
            >>> std = Student()
            >>> std.tostring() # output: 'Student Class'
            ```
