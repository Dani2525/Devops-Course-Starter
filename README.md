# DevOps Apprenticeship: Project Exercise

## System Requirements

The project uses poetry for Python to create an isolated environment and manage package dependencies. To prepare your system, ensure you have an official distribution of Python version 3.7+ and install Poetry using one of the following commands (as instructed by the [poetry documentation](https://python-poetry.org/docs/#system-requirements)):

### Poetry installation (Bash)

```bash
curl -sSL https://raw.githubusercontent.com/python-poetry/poetry/master/install-poetry.py | python -
```

### Poetry installation (PowerShell)

```powershell
(Invoke-WebRequest -Uri https://raw.githubusercontent.com/python-poetry/poetry/master/install-poetry.py -UseBasicParsing).Content | python -
```

## Dependencies

The project uses a virtual environment to isolate package dependencies. To create the virtual environment and install required packages, run the following from your preferred shell:

```bash
$ poetry install
```

You'll also need to clone a new `.env` file from the `.env.template` to store local configuration options. This is a one-time operation on first setup:

```bash
$ cp .env.template .env  # (first time only)
```

The `.env` file is used by flask to set environment variables when running `flask run`. This enables things like development mode (which also enables features like hot reloading when you make a file change). There's also a [SECRET_KEY](https://flask.palletsprojects.com/en/1.1.x/config/#SECRET_KEY) variable which is used to encrypt the flask session cookie.


## new Environment variables

SECRET_KEY=secret-key
TRELLO_BOARDID=trello-id
TRELLO_KEY=trello-key
TRELLO_TOKEN=trello-token
TRELLO_LISTID1=trello-listid1
TRELLO_LISTID2=trello-listid2

## Running the App

Once the all dependencies have been installed, start the Flask app in development mode within the Poetry environment by running:
```bash
$ poetry run flask run
```

You should see output similar to the following:
```bash
 * Serving Flask app "app" (lazy loading)
 * Environment: development
 * Debug mode: on
 * Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)
 * Restarting with fsevents reloader
 * Debugger is active!
 * Debugger PIN: 226-556-590
```
Now visit [`http://localhost:5000/`](http://localhost:5000/) in your web browser to view the app.

## Running tests

You should run the command "poetry run pytest" to run all the tests that are assocoiated with this todoapp.

## how to build and run development and production containers

build and run production containers by running these commands
docker build --target production --tag todo-app:prod .
docker run --env-file .env -p 5000:5000 todo-app:prod 

build and run development containers by running these commands
docker build --tag todo-app .  
docker run --env-file .env todo_app

## running test container 
test container run using CI pipeline in My-CI-Pipeline.yml file everytime you open or reopen a pull request or push to repository
can also be observed on GitHub workflows to see which ones pass and fail.
