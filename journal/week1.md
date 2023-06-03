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

# This will run the backend-flask module in python.
# python3 -m flask run --host=0.0.0.0 --port=4567
CMD [ "python3", "-m" , "flask", "run", "--host=0.0.0.0", "--port=4567"]
```

### 2. Build Container
```
docker build -t  backend-flask ./backend-flask
```
Below is a screenshot of my Gitpod showing the backend-flask image.
![Backend Image](assets/build%20backend%20container%20code%20result.PNG)

### 3. Run Container
```
docker run --rm -p 4567:4567 -it backend-flask
FRONTEND_URL="*" BACKEND_URL="*" docker run --rm -p 4567:4567 -it backend-flask
export FRONTEND_URL="*"
export BACKEND_URL="*"
docker run --rm -p 4567:4567 -it -e FRONTEND_URL='*' -e BACKEND_URL='*' backend-flask
docker run --rm -p 4567:4567 -it  -e FRONTEND_URL -e BACKEND_URL backend-flask
unset FRONTEND_URL="*"
unset BACKEND_URL="*"
```

### 4. Containerize Frontend
#### Run NPM Install
We need to do this before building the container because it needs to copy the contents of node_modules.
```
cd frontend-react-js
npm i
```
#### Create Dockerfile
![Frontend Dockerfile](assets/frontend%20docker%20file.PNG)
