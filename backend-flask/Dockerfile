FROM python:3.10-slim-buster

# Inside Container
# create and set working directory within container (to be used for subsequent commands)
WORKDIR /backend-flask

# Outside Container -> Inside Container
# copy/paste req.s file from host directory (outside) into container directory (inside)
COPY requirements.txt requirements.txt

# Inside Container
# install Python dependencies (libraries) on container
RUN pip3 install -r requirements.txt

# Outside Container -> Inside Container
# "." means everything in current directory
# first . means /backend-flask (outside container)
# second . means /backend-flask (inside container)
COPY . .

# Inside container
# Sets environmental variables (env vars) for entire environment; will remain set while the container is running
ENV FLASK_ENV=development

EXPOSE ${PORT}

# CMD (Command)
# Runs the flask app
# python3 - distinguishes python version 3
# -m, flask - module flag; shortcut way to run flask
# run - run that module
# --host=0.0.0.0 - binding to 0.0.0.0, used to expose app outside of current environment; the "everything address"; necessary to define this when running in a container
# --port=4567 - start on port 4567, instead of others (e.g. 3000, 8080, 8000, etc. based on framework's default) 
# python3 -m flask run --host=0.0.0.0 --port=4567
CMD [ "python3", "-m" , "flask", "run", "--host=0.0.0.0", "--port=4567"]