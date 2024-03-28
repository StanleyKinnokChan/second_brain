
### Environment
Window:
```
python3 -m venv env
cd env
.\Scripts\activate.bat
cd ..

```
c:\\Users\\StanleyChan\\AppData\\Local\\Programs\\Python\\Python38\\python.exe  -m venv env

Ubuntu
```
python3 -m venv env
source env\Scripts\activate
```

### Package
Output installed packages in requirements format.
```
python -m pip freeze
```

To install packages in requirements format
```
py -m pip install -r requirements.txt
```

Generate a requirements file and then install from it in another environment.
```
env1\\bin\\python -m pip freeze > requirements.txt
env2\\bin\\python -m pip install -r requirements.txt
```

Rereference:
https://pip.pypa.io/en/stable/cli/pip_freeze/