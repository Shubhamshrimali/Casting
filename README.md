INTRODUCTION

This project is the final project for the Udacity Full Stack Developer Nano Degree.The project is to simulate a casting agency. This includes having actors and movies and assigning actors to movies.This project has two models/tables: A movie table that holds all the movies and an actors table that holds all the actors. For each movie, there are many actors so there is a one to many relationship there. 

MOTIVATION

Udacity give faculty teach the concept in very easy way. That anybody can understand easily and start working on the technology. This help to get confidance to work on the project and improve the skills.

INSTRUCTION

To login or set up an account, go to the following url: 

https://devcoffe.auth0.com/authorize?audience=https://moneyfistcasting2020.herokuapp.com/&response_type=token&client_id=FJ6I6cc01QVcgcM7Vgna3OVKzZHm6DbW0&redirect_uri=https://moneyfistcasting2020.herokuapp.com/

There are three roles within the API. Casting Assistant, Casting Director and Executive Producer. The logins for the three roles has been provided in the separate notes 

The url for the API:
https://moneyfistcasting2020.herokuapp.com/

Installing Dependencies

Python 3.7
Follow instructions to install the latest version of python for your platform in the python docs

Virtual Environment,
We recommend working within a virtual environment whenever using Python for projects. This keeps your dependencies for each project separate and organaized. Instructions for setting up a virual enviornment for your platform can be found in the python docs

PIP Dependencies
Once you have your virtual environment setup and running, install dependencies by naviging to the /backend directory and running:

pip install -r requirements.txt
This will install all of the required packages we selected within the requirements.txt file.

Database Setup
To set up empty DB run alembic upgrade

flask db upgrade
With Postgres running and to run tests, restore a database file provided. From the folder in terminal run. 

User Abilities

Actors
create:actor: Ability to permit creation of a new actor to insert into the DB
read:actor: Ability to permit retrieving actors infos
update:actor: Ability to permit edit an actor infos
delete:actor: Ability to remove an actor from the DB

Movies
create:movie: Ability to permit creation of a new movie to insert into the DB
read:movie: Ability to permit retrieving movies infos
update:movie: Ability to permit edit a movie infos
delete:movie: Ability to remove a movie from the DB

User Roles

assistant: Help casting director to analyze actors and movies info. Has following abilities:
read:actor
read:movie

director: Take decisions about actors and can update movies data. Abilities:
create:actor
read:actor
update:actor
delete:actor
read:movie
update:movie

executive-producer: Can manage everything. Abilities:
create:actor
read:actor
update:actor
delete:actor
create:movie
read:movie
update:movie
delete:movie
API Endpoints
Actors
POST /actors
Endpoint to add a new actor in the DB. You need create:actor ability.

JSON parameters:

name: Name of the actor
age: Age of the actor
gender: Gender of the actor. Admitted values are "male", "female" or "other"
Example JSON request:

{
    "id": 1,
    "name": "Salman",
    "age": 34,
    "gender: "male",
    "movies":[]
}
GET /actors
Endpoint to get list of actors. You need read:actor ability.

Query parameters:

search_term: String to filter actors by their name. Search is case insensitive
page: As the result is paginated, this parameter specify the page to retrieve
per_page: As the result is paginated, this specify how many items get per page (max 50)
Example JSON response:

{
    "items": [
        {
            "id": 1,
            "name": "Salman",
            "age": 34,
            "gender: "male",
            "movies":[]
        },
        {
            "id": 2,
            "name": "Amitab",
            "age": 120,
            "gender: "other",
            "movies": [
                {
                    "id": 1,
                    "title": "Transformers",
                    "release_date": "2007-09-21"
                }
            ]
        },
        ...,
    ],
    "total_items": 25,
    "page": 1,
    "pages": 3
}
GET /actors/:actor_id
Endpoint to get a specific actor. You need read:actor ability.

URL parameters:

actor_id: Id of actor to retrieve
Example JSON response:

 {
    "id": 2,
    "name": "Amitab",
    "age": 120,
    "gender: "other",
    "movies": [
        {
            "id": 1,
            "title": "Transformers",
            "release_date": "2007-09-21"
        }
    ]
}
PATCH /actors/:actor_id
Endpoint to edit an actor data. You need update:actor ability.

URL parameters:

actor_id: Id of actor to edit
JSON parameters:

name: New name of the actor
age: New age of the actor
gender: New gender of the actor. Admitted values are "male", "female" or "other"
Example JSON request:

{
    "Name "Deppika",
    "gender": "female",
}
Example JSON response:

{
    "id": 1,
    "name": "Deppika",
    "age": 34,
    "gender": "female",
}
DELETE /actors/:actor_id
Endpoint to remove an actor from the DB. You need delete:actor ability.

URL parameters:

actor_id: Id of actor to delete
Movies
POST /movies
Endpoint to add a new movie in the DB. You need create:movie ability.

JSON parameters:

title: Title of the movie
release_date: Date of release
Example JSON request:

{
    "title "PK",
    "release_date": "2007-09-21",
}
Example JSON response:

{
    {
        "id": 1,
        "title": "PK",
        "release_date": "2007-09-21",
        "actors": []
    }
}
GET /movies
Endpoint to get list of movies. You need read:movie ability.

Query parameters:

search_term: String to filter movies by their title. Search is case insensitive
page: As the result is paginated, this parameter specify the page to retrieve
per_page: As the result is paginated, this specify how many items get per page (max 50)
Example JSON request:

{
    "items": [
        {
            "id": 1,
            "title": "PK",
            "release_date": "2007-09-21",
            "actors": [
                {
                    "id": 2,
                    "name": "Amitab",
                    "age": 120,
                    "gender: "other"
                }
            ]
        },
        ...,
    ],
    "total_items": 12,
    "page": 1,
    "pages": 2
}
GET /movies/:movie_id
Endpoint to get a specific movie. You need read:movie ability.

URL parameters:

movie_id: Id of movie to retrieve
Example JSON response:

{
    "id": 1,
    "title": "PK",
    "release_date": "2007-09-21",
    "actors": [
        {
            "id": 2,
            "name": "Amitab",
            "age": 120,
            "gender: "other"
        }
    ]
}
PATCH /movies/:movie_id
Endpoint to edit an movie data. You need update:movie ability.

URL parameters:

movie_id: Id of movie to edit
JSON parameters:

title: New title fo the movie
release_date: New release date of the movie

DELETE /movies/:movie_id
Endpoint to remove an movie from the DB. You need delete:movie ability.

URL parameters:

movie_id: Id of movie to delete
