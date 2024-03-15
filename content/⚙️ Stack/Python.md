# Python

- error handling

    [[Python/Untitled.png]]

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

- parenthesis on function and class
    - With parenthesis: call the function
    - Without parenthesis: reference **the function (point it to a variable)
- API
    - what is API
        - communication layer between systems without understanding exactly what each other does
        - calling a API = request from a user + response from the server
    - terminology
        - **Base/API URL:** the url allows you to fetch data from
        - **endpoint:**  is a part of the URL that specifies what **resource** you want to fetch. Well-documented APIs usually contain an **API reference**, which is extremely useful for knowing the exact endpoints and resources an API has and how to use them.
        - **consume an API:** use any part of it from your application
    - type of API
        1. **SOAP (Simple Object Access Protocol)** is typically associated with the enterprise world, has a stricter contract-based usage, and is mostly designed around actions. High security
        2. **REST (Representational State Transfer)**
            - is typically used for public APIs and is ideal for fetching data from the web. It’s much lighter and closer to the HTTP specification than SOAP. majority of public APIs are still REST APIs
            - uniform way of interacting with a given server regardless of device or application type using HTTP requests method (get, post, pull, delete)
        3. GraphQL is on the rise and is being adopted by bigger and bigger companies
    - how to call in python
        - install requests package in cmd `$ python -m pip install requests`

        ```python
        import requests
        import json
        import pandas as pd

        #base url + endpoint, use dicts when header and params are needed
        response = requests.get("https://api.thedogapi.com/v1/breeds").json() #.json() print a human-friendly Json format

        data=json.loads(response.text)   #convert Json string into a Python Dictionary; aka "deserialization"
        pd.json_normalize(data) #flatten the nested df + convert into pd_df, neeeded Unserialized data
        ```

    - Authentication
        - **API key:**
            - most common level of authentication, the key is open to public or given to you via specific method (eg email to you after registration on the website)

                ```python
                #example of API key, put the key in the dictionary and pass it into the params argument

                endpoint = "https://api.nasa.gov/mars-photos/api/v1/rovers/curiosity/photos"
                # Replace DEMO_KEY below with your own key if you generated one.
                api_key = "DEMO_KEY"
                query_params = {"api_key": api_key, "earth_date": "2020-07-01"}
                response = requests.get(endpoint, params=query_params)
                response
                ```

        - OAuth:
            - another very common standard but more secure.
            - The server ask the user info. from the 3rd-party and if user pass the credentail identification (eg log-in) the server will send the response for the user request

            ```python
            # Authenticating with OAuth2 in Requests
            from requests_oauthlib import OAuth2Session

            # Inlcude your data
            client_id = "include your client_id here"
            client_secret = "include your client_secret here"
            redirect_uri = "include your redirect URI here"

            # Create a session object
            oauth = OAuth2Session(client_id, redirect_uri = redirect_uri)

            # Fetch a token
            token = oauth.fetch_token("<url to fetch access token>", client_secret = client_secret)

            # Get your authenticated response
            response = oauth.get("URL to the resource")
            ```
