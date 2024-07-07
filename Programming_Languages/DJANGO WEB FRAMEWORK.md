how to create, design, and configure a web app using the Django framework
You will explore more on: 

 * Models: and how to handle their relationship to databases. 
 * Views: You will use them to render requested data to the templates for the user interface
* Django templating and best practices.

To start a django app use:
```
python manage.py start myApp
```

When setting up a python application, it is recommended to use a  virtual environment.
A python environment is an isolated environment having it's copy of the interpreter and libraries so that there's no clash with the global installation of python.
The python virtual environment is set-up with the ``venv`` built-in model.
***To setup a virtual environment***
```
python -m venv myvenv
//python3 -m venv(built in module)  name_of_module
```
***To activate***
```
source myenv/bin/activate
```
After setting up  and activating the virtual environment, install django framework:
```
pip install django
```
Checking libraries:
``pip freeze``
Append libraries in a requirement.txt file
``pip freeze > requirements.txt``
Install libraries listed in the requirement.txt file:
``pip install -r requirement.txt``
