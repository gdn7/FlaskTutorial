### Flaskr
#### Install App [[Link](https://flask.palletsprojects.com/en/1.1.x/tutorial/install/)]
```bash
pip install -e .
```
This tells pip to find setup.py in the current directory and install it in editable or development mode. Editable mode means that as you make changes to your local code, you’ll only need to re-install if you change the metadata about the project, such as its dependencies.

You can observe that the project is now installed with pip list.

```
$ pip list

Package        Version   Location
-------------- --------- ----------------------------------
click          6.7
Flask          1.0
flaskr         1.0.0     /home/user/Projects/flask-tutorial
itsdangerous   0.24
Jinja2         2.10
MarkupSafe     1.0
pip            9.0.3
setuptools     39.0.1
Werkzeug       0.14.1
wheel          0.30.0
```

Nothing changes from how you’ve been running your project so far. FLASK_APP is still set to flaskr and flask run still runs the application, but you can call it from anywhere, not just the flask-tutorial directory.

___
#### Testing [[Link](https://flask.palletsprojects.com/en/1.1.x/tutorial/tests/)]
```bash
# To run the tests, use the pytest command.
pytest

# To measure the code coverage of your tests, use the coverage command to run pytest instead of running it directly.
coverage run -m pytest

# You can either view a simple coverage report in the terminal:
coverage report
```

___
#### Deploy [[Link](https://flask.palletsprojects.com/en/1.1.x/tutorial/deploy/)]
Pack everything on local machine.
```bash
pip install wheel
python setup.py bdist_wheel
```

Copy `dist/flaskr-1.0.0-py3-none-any.whl` to server machine.
```bash
pip install flaskr-1.0.0-py3-none-any.whl

export FLASK_APP=flaskr
flask init-db
```

Build a secret key
```bash
python -c 'import os; print(os.urandom(16))'
# e.g. output b'_5#y2L"F4Q8z\n\xec]/'
```

Add the following line to `config.py`:
```
vim venv/var/flaskr-instance/config.py
SECRET_KEY = b'_5#y2L"F4Q8z\n\xec]/'
```

___
#### Production Server
Use a production WSGI server.
```
$ pip install waitress
$ waitress-serve --call 'flaskr:create_app'
Serving on http://0.0.0.0:8080
```

___
#### References
* Tutorial [[Link](https://flask.palletsprojects.com/en/1.0.x/tutorial/)]
* Command Line Interface [[Link](https://flask.palletsprojects.com/en/1.1.x/cli/#cli)]
