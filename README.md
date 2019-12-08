# Online Snake Game

References:  
Jenkins: **34.89.51.152:8080**  
Flask: **34.76.185.11:5001**  
Pytest-coverage: **34.76.185.11:5001/coverage**  
Trello-board: **https://trello.com/b/Ek1HhDcU/individual-project-plan**  
<br><br><br><br><br><br><br><br>


# Original Project Idea
Allow a user to register then login, play a snake game which would record their score and save onto a database, and allow the user to view his scores as well as the user with the highest score.

The snake game would involve user manipulating an entity on a arena, the user would be able to collect fruits which would increase the length of the snake entity, and increase the user's score. If the snake entity hit the edge of the arena, the game would be over.

## Original ERD diagram
![ERD diagram](/images/ERD.png)
Player would have a one to many relationship with Scores.  
Account details would have a one-to-one relationship with Player.

<br>

## Original Use Case Diagram
![use case diagram](/images/UseCase.png)

# What I got
The Use case and the functionality of the original project idea is essentially completely intact to that of what I had envisioned, however I have decided to change the database as I thought one of the tables was redundant.

## New ERD diagram
![ERD new diagram](/images/ERDnew.png)
Now there are simply two tables with Account details filling the void of what Player table was doing previously.  
Account details has a one-to-many relationship with Scores table.

## Had to switch to websocket for game connection

# Testing
Testing was done using pytest and a coverage has also been supplied. Look at *References* for the link to the coverage.  
<br>
74% coverage was achieved.  
11 tests total have been created and executed; 3 of which were used to test the snake game, and the rest were used to test the website and database functionality.  
Coverage may further be increased if integration testing could be performed, such as using Selenium to test the more user-dependant functionalities such as being able to login, test the forms, test the jinja2 code, etc...  

The snake game is an interesting creation. It is a simple application, however it is multi-threaded, meaning that conventional testing schemes such as Unit testing or Integration testing may not fully apply due to the nature of parallel systems. Ideally you would use a test package suited for multi-threaded testing, such as some sort of spec=flow analysis which would calculate all possible states each of the threads could be in to see whether a deadlock or a livelock has occured.  
However, I have still included some minor tests for the snake game specifically by creating an instance of it and simply waiting to see what would happen. In theory, after a certain amount of time, the snake would hit the outer edges of the arena, thereby changing the game state variable which I would then be able to test.

# Deployment Overview
![techs used](/images/tech.png)
Made a webserver application using Python, MySQL, and Flask. Used git and github for version control whilst using Trello to organise myself. Github would submit requests to Jenkins to update, test using pytest, and redeploy the application. Finally, the cloud provide, GCP, was used to host the application.

Technologies used:  
Python/Mysql/Flask
Git/Github  
Trello  
Jenkins  
Pytest  
GCP  

# The Future
Many things could be improved. For example, I am not really sure how multi-threading is done under the hood in Python, so whether my snake game is thread safe is unknown at this point, so more research would definitely help. In terms of looks, the website looks pretty barebones, perhaps integrating a front-end View framework such as Bootstrap would be a good idea.  
Further expanding the game would be interesting, such as adding multi-player functionality wherein two snakes would be in the same arena, and the one that hits the others' tail loses. 


