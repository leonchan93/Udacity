# Capstone Final Project

### 1. Motivations

The motivation for this project was to utilise all of the concepts and skills taught from the previous lessons and dispaly them here in this project. The project requirement was to build and API from start to finish and to hos it. The following skills were demonstrated in this project;

- Coding in Python 3
- Relational Database Architecture
- Modeling Data Objects with SQLAlchemy
- Internet Protocols and Communication
- Developing a Flask API
- Authentication and Access
- Authentication with Auth0
- Authentication in Flask
- Role-Based Access Control (RBAC)
- Testing Flask Applications
- Deploying Applications

Using these skills, an application was built that was based around a casting agency company that creates movies and assigning actors to those movies. A system needed to be created to streamline this process and involved creating an 'actors' and 'movies' models in a database that took in the required attributes. Endpoint API's needed to be created to manipulate the data created, this came in the form of GET, POST, DELETE and PATCH requests.Authentication and access permissions needed to also be created depending on if the user of this application was a casting assistant, casting director or executive producer, with differing permissions depending on the users role. The API's needed to be tested along with the permissions needed to access them. Fainlly, the application used Heroku to deploy onto a cloud platform. 

### 2. URL location for the hosted API

The URL of the hosted application is: https://lccapstoneproject.herokuapp.com/

### 3. Cloning Repository 

To begin the project clonde the starter code into your local machine using:

```bash
git clone https://github.com/leonchan93/Udacity.git
cd projects/capstone/starter_code 
```

### 4. Tech Stack (Dependencies) Project dependencies, local development and hosting instructions,

We will be using **Python 3.7** in our application. Follow instructions to install the latest version of [python docs](https://docs.python.org/3/using/unix.html#getting-and-installing-the-latest-version-of-python)

**virtualenv** We will be using a virtual environment to create an isolated Python environment in order to run the application. To initialise and activate the virtualenv (for Windows) use:

```bash
python -m virtualenv env
source env/Scripts/activate
```
For more information on creating and activating virtual environments visit:[python docs](https://packaging.python.org/guides/installing-using-pip-and-virtual-environments/)

**PIP Dependencies** The tech stack that will be used for this application is outlined in the requirements.txt file. 
To install the dependencies simply input the command:

```bash
pip install -r requirements.txt
```

### 5. Database Setup

In order to run the models in the database the user must first have postgres installed. Use the following command to isntall postgres:

```bash
pip install postges
```

The database being used is called 'castingagency' and the user is 'postgres'. To create the dummy data inside the database use the commands:

```bash
export FLASK_ENV="development"
export FLASK_APP="app"
flask shell
from models import setup_db, Actors, Movies, db_drop_and_create_all, create_dummy_data
db_drop_and_create_all()
create_dummy_data()
```

### 6. Running Development Server 

To run the development server, use the commands below:

```bash
export FLASK_APP=myapp
export FLASK_ENV=development # enables debug mode
flask run --reload # Using reload will let Flask know to refresh the application everytime a change is made
```

### 7. Auth0 Access and Authorisation

Auth0 was used by the website Auth0. This site allowed for the created of a login page for a single page application and also allowed for creation of a JWT token which gave permissions and access to API endpoints to specific roles that were assigned to users. These were also created in Auth0. The roles and their corresponding permissions were:

#Casting Assistant

With permission to API's:

```bash
get:actors
get:movies
```
#Casting Director

With permission to API's:

```bash
delete:actor	
delete:actors		
get:actors	
get:movies	
patch:actors	
patch:movies	
post:actors
```
#Executive Producer

With permission to API's:

```bash
delete:actor		
delete:actors		
delete:movies		
get:actors		
get:movies		
patch:actors	
patch:movies	
post:actors	
post:movies
```
###  8. Documentation of API behavior and RBAC controls

#Endpoints

The endpoints are organised around REST.  It accepts form-encoded request bodies and returns JSON-encoded responses.

1. Base URL: http://127.0.0.1:5000

2. Errors: This application  uses conventional HTTP responses to show the success or failure of an API request

```
HTTP Status Code Summary 

200 - OK

400 - Bad request

402 - Request Failed

404 - Not Found 

500 - Server Error 

403 - Unauthorised
```

#GET Request /actors - This gets the actors from the database

curl -s -H "Authorization: Bearer {TOKEN}" -X GET http://127.0.0.1:5000/actors

```
{"actors":[{"age":20,"gender":"Male","id":1,"name":"Test1"},{"age":30,"gender":"Male","id":5,"name":"actor3"},{"age":20,"gender":"Male","id":12,"name":"Test"},{"age":20,"gender":"Male","id":13,"name":"TestWhat colour is grass?"},{"age":20,"gender":"Male","id":14,"name":"TestWhat colour is grass?"},{"age":20,"gender":"Male","id":15,"name":"TestWhat colour is grass?"},{"age":20,"gender":"Male","id":16,"name":"TestWhat colour is grass?"},{"age":20,"gender":"Male","id":17,"name":"TestWhat colour is grass?"},{"age":20,"gender":"Male","id":18,"name":"TestWhat colour is grass?"},{"age":20,"gender":"Male","id":19,"name":"Test"}],"success":true,"total_actors":46}
```