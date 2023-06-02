# Week 1 — App Containerization

## Lecture Procedures

### 1. Add Dockerfile
```
FROM python:3.10-slim-buster

# Inside Container
# make a new folder inside container
WORKDIR /backend-flask

# Outside Container -> Inside Container
# this contains the libraries we want to install to run the app
COPY requirements.txt requirements.txt

# Inside Container
# Install the python libraries used for the app
RUN pip3 install -r requirements.txt

# Outside Container -> Inside Container
# The . means everything in the current directory
# first period means everything in /backend-flask (outside container)
# second periond means everyhting in /backend-flask (inside container)
COPY . .

# Set Environment Variables (Env Vars for short)
# Inside Container and will remain set when the container is running
ENV FLASK_ENV=development

EXPOSE ${PORT}

# CMD = Command
# python3 -m flask run --host=0.0.0.0 --port=4567
# -m flask is using the flask module
CMD [ "python3", "-m" , "flask", "run", "--host=0.0.0.0", "--port=4567"]
```

### 2. Build Container
```
docker build -t  backend-flask ./backend-flask
```
![Backend Image](/assets/build%20backend%20container%20code%20result.PNG)

### 3. Run Container
```

```

Run in background
```

```
